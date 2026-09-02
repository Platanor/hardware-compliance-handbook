# Secure OTA update architecture beyond image signing

This is a technical reference on OTA update architecture: partition schemes, update-metadata trust models, signing algorithm trade-offs, delta updates, and failure recovery. It assumes the basics - why image signing matters, how MCUboot handles it on Nordic/STM32 - already covered in the blog article `secure-ota-updates-iot-firmware`, and goes deeper on what a production-grade update pipeline actually needs beyond "the image is signed."

Relevant hooks: CRA Annex I, Part I, point 2(c) (automatic updates with an opt-out) and Part II, points 7 (secure update-distribution channels) and 8 (updates free of charge) - see `cra/essential-requirements.md` for the verified regulatory text.

## A/B partitioning vs. in-place updates

The core problem is atomicity: a device has to end up either fully on the new firmware or fully on the previous known-good version, never in between.

A single-partition, in-place update overwrites the active firmware directly. A power loss, hardware reset, or connection drop mid-write leaves the device with a partially erased or partially written image - and since the interrupt vector table and firmware headers can themselves be the corrupted bytes, the ROM bootloader has nothing valid to hand control to. That's a bricked device, recoverable (if at all) only through a physical JTAG/SWD/UART recovery procedure.

A/B (dual-bank) partitioning splits storage into two independent slots: an active slot the device currently boots and runs from, and an inactive slot that receives the new image. Writes during an OTA session only touch the inactive slot; the active slot keeps running the device throughout. A power failure at any point during the write leaves the active slot completely untouched. Only after the write completes and the new image's cryptographic signature and integrity are verified does the bootloader flip a control flag (in NVRAM or a bootloader control block) marking the inactive slot as the next boot target.

The tradeoff is direct: A/B needs roughly double the flash budget for whatever it's duplicating (root filesystem, kernel, device tree, or a monolithic MCU image), which is a real BOM cost at volume - moving from 4 GB to 8 GB eMMC, or from 512 KB to 1 MB of MCU flash, has a per-unit cost that multiplies across a production run. In practice that cost is usually smaller than the alternative: field returns, truck rolls, or manual JTAG/UART recovery for bricked units.

| | Single-partition in-place | A/B (dual-bank) | Streaming A/B |
|---|---|---|---|
| Flash cost | 1x | 2x | 2x, no separate staging area |
| Update atomicity | None - high brick risk | Full | Full |
| Staging area needed | Yes, if verifying before write | No - writes go straight to the inactive slot | No |
| Downtime | Erase + write + boot | Just the reboot | Just the reboot |
| Bootloader complexity | Low | Higher (counter/flag management) | Higher |

**Embedded Linux frameworks** implementing this pattern, each with real differences worth knowing before picking one:

- **RAUC** - a lightweight C daemon (Pengutronix) built around a "slot" abstraction that can model complex topologies (parent/child slots covering rootfs, bootloader, and an FPGA bitstream together). Updates ship as SquashFS bundles signed with X.509/CMS, and RAUC integrates with dm-verity for runtime tamper protection and supports streaming installs.
- **Mender** - a client/server product with a strict A/B rootfs state machine as its core model; a C++ client keeps the resource footprint down. Extended functionality (container updates, single-file updates) goes through its Update Modules mechanism rather than being baked into the core.
- **SWUpdate** - a modular framework processing `.swu` bundles (CPIO archives) through a set of pluggable handlers, flexible enough to mix A/B rootfs updates with delta patches and single-filesystem in-place updates in the same pipeline, and integrates with Eclipse hawkBit for fleet management.

**On MCUs**, MCUboot is the common bootloader, and it supports two different mechanics for the same A/B idea: **swap mode**, where on a confirmed update the contents of the two slots are exchanged block-by-block through a scratch area (lets code run from a fixed, single address without position-independent linking, at the cost of extra flash wear and boot-time copy latency), and **Direct-XIP**, where the image for each slot is built and signed for that slot's own base address, and the bootloader simply picks whichever slot holds the valid, higher-versioned image and jumps straight to it - no data movement at all, at the cost of maintaining two separately linked build artifacts (or position-independent code) instead of one. Some SoCs separately offer a hardware bank-remap register (for example on Nordic nRF9160, or STM32 parts with dual-bank swap) that lets a single build run unmodified regardless of which physical bank is active; that's a distinct hardware feature some designs combine with an A/B scheme, not a requirement for MCUboot's own Direct-XIP mode.

## Trust model: why a single signature isn't enough

Verifying a signature on the firmware image itself stops a modified or unsigned image from installing. It does not stop several other attacks that operate one level up, against the update *metadata and delivery process*:

- **Rollback** - an attacker feeds the device an old, still-validly-signed image with a known vulnerability.
- **Freeze** - an attacker (via MITM or a compromised CDN) keeps serving the device a stale-but-validly-signed manifest indefinitely, so the device believes it's already current and never receives the actual patch.
- **Mix-and-match** - in a multi-component system, an attacker combines binaries from two different valid releases (say, a kernel from one release paired with a rootfs from another) into a combination that was never tested or released as a unit.
- **Slow retrieval** - an attacker deliberately throttles delivery to exhaust device resources or keep it in a vulnerable state longer than necessary.

**The Update Framework (TUF)** addresses this with a manifest structure that separates responsibilities across four roles, each independently signed:

- **Root** - the trust anchor. Signs the public keys for every other role, held offline (HSM or air-gapped), responsible for key rotation.
- **Targets** - lists the hashes and sizes of available firmware images, protecting against binary substitution.
- **Snapshot** - signs a manifest of the current Targets file's version and hash, which is what actually closes off mix-and-match attacks (a stale or substituted Targets file no longer matches what Snapshot attests to).
- **Timestamp** - a short-lived (commonly around a day) pointer to the current Snapshot, which is what defeats freeze attacks - an attacker serving a stale bundle can't produce a Timestamp signed recently enough to still be considered valid.

TUF also supports threshold signatures (N-of-M keys required to approve a release, e.g. two security engineers' keys), which is a meaningful mitigation against a single compromised signing key.

**Uptane** adapts TUF for fleets of resource-constrained, often non-internet-connected nodes - the paradigm case is automotive ECUs on CAN/LIN/FlexRay, but the same shape applies to any hub-and-spoke IoT topology with a gateway device and constrained peripherals behind it. Two adaptations matter:

**Split repositories.** An **Image Repository**, owned by the OEM/developer, approves valid binaries using offline keys - compromising the online serving infrastructure alone can't produce a validly-signed malicious image. A **Director Repository**, an online automated system, decides which approved image goes to which specific device (by VIN, hardware serial, etc.) using online keys for fast per-device targeting. An attacker needs to compromise *both* the online Director and the offline Image repository to push malicious code - splitting one high-value target into two, one of which is intentionally hard to reach.

**Primary/Secondary device hierarchy.** A Primary node (network-connected, enough compute and storage to hold and verify metadata from both repositories) distributes verified images to Secondary nodes over an internal bus. Per the Uptane standard, a Primary must perform full verification; a Secondary should perform full verification and, only if it genuinely can't (an 8-bit MCU with a few KB of RAM is the typical reason), falls back to partial verification - checking only the Director repository's signature on a reduced manifest handed to it by the Primary. Partial verification blocks arbitrary code substitution but does trust the Primary's word on what the Director actually said, which is the residual risk if the Primary itself is fully compromised.

## Signing algorithm choice: Ed25519 vs. RSA

Verification cost matters directly on an MCU without a hardware crypto accelerator - it affects boot time, RAM/stack usage, and flash budget for the crypto library itself.

RSA's security rests on integer factorization; Ed25519 (EdDSA over Curve25519) operates over a 255-bit prime field. At roughly equivalent security levels, the practical footprint differs by an order of magnitude in several dimensions: an Ed25519 public key and signature are 32 and 64 bytes respectively, versus a 512-byte (4096-bit) modulus and a 512-byte signature for RSA-4096 - the actual encoded public key (modulus plus exponent, typically DER-wrapped) runs somewhat larger than the bare 512-byte modulus. RSA-4096 verification on a 32-bit MCU without hardware acceleration needs to multiply arrays of 128 32-bit words and run Montgomery reduction over that width, which costs meaningfully more CPU time and needs several KB more RAM for intermediate buffers than Ed25519's fixed 256-bit (8-word) operations - on a part with limited total SRAM, that gap can be the difference between fitting the crypto library's working set and a stack overflow. There's a common misconception that RSA verifies faster because of its small public exponent (65537 = 2^16+1, needing only 17 modular multiplications for exponentiation) - that advantage is real on 64-bit desktop hardware but is outweighed on constrained 32-bit MCUs by the wide-integer multiplication cost.

Ed25519 is also constant-time by construction, which matters for side-channel resistance; RSA implementations need explicit blinding to get the same property.

The practical guidance: Ed25519 is the sane default for new embedded designs - smaller manifest headers, lower RAM pressure, side-channel resistance without extra engineering. RSA-4096 remains the right choice mainly where a legacy toolchain or a specific compliance requirement (e.g. a certified HSM whose approved algorithm list hasn't caught up to EdDSA) forces it.

## TLS protects the channel, not the artifact

A recurring architectural mistake: treating delivery over HTTPS as sufficient and skipping a separate signature on the firmware image itself.

**Channel security** (TLS/HTTPS) authenticates a network endpoint via X.509 and encrypts data in transit. It protects against passive eavesdropping and tampering by intermediate network nodes. **Content security** is a separate, transport-independent property: a cryptographic signature on the artifact itself, verifiable regardless of whether it arrived over HTTPS, USB, LoRaWAN, or satellite link.

Relying on TLS alone breaks down in scenarios where the channel is legitimately trusted but the artifact it's carrying isn't:

- **A compromised CDN or object-storage bucket.** If an attacker gets write access to the CDN or S3-equivalent serving firmware, the device's TLS handshake with that CDN succeeds normally - the certificate is valid, the connection is genuinely encrypted - while the payload itself has been swapped for a malicious image.
- **Enterprise TLS interception.** Industrial networks commonly run deep-packet-inspection proxies that terminate and re-originate TLS using an internally trusted CA. If a device's trust store includes that corporate CA (intentionally, for network compatibility), the proxy can transparently substitute traffic content.
- **A compromised or mis-issued root CA.** Any CA in the device's trust store being compromised or improperly issuing a certificate enables a MITM presenting a validly-chained certificate for malicious content.

The fix is architectural, not a configuration tweak: an end-to-end signature on the update artifact, verified on-device independent of the transport it arrived over, is a separate control from TLS - not a redundant one.

## Delta (differential) updates

At fleet scale over constrained links (NB-IoT, LTE-M, satellite), shipping full images - a 500 MB-2 GB embedded Linux rootfs, or even a multi-MB MCU image - gets expensive fast. Delta updates ship only the difference between the currently-running image and the target image, typically cutting transferred bytes by 70-95%.

Common tooling: **bsdiff/bspatch** for binary diffing using suffix-array-based matching; **casync**, which content-addresses variable-size chunks so only the chunks actually missing locally need to be fetched; and **libostree (OSTree)**, often described as "git for binaries" - it tracks a filesystem object graph and transfers only changed files and their binary diffs.

The complexity this buys back is real and worth naming plainly:

**Strict baseline dependency.** A delta patch is computed against a specific known starting image. If the device's actual current state has drifted by even one bit from that assumed baseline (a bad flash sector, a manual file modification, a partially-applied prior update), applying the patch either fails outright or - worse - silently produces a corrupted target image.

**Multi-phase verification is mandatory, not optional.** A correct pipeline: (1) hash the currently active partition and confirm it matches the manifest's declared baseline hash *before* applying anything; (2) apply the patch while streaming from the active slot into the inactive one; (3) hash the reconstructed inactive slot and confirm it matches the manifest's target hash. Skipping step 1 is how baseline drift turns into a corrupted device instead of a caught error.

**Resource cost.** Patch reconstruction needs RAM for working buffers and real CPU time; on an MCU with tens of KB of RAM, reconstructing a complex binary patch can itself be the constraining factor.

**A full-image fallback path is required, not optional.** If the baseline hash check in step 1 fails, the client needs to abandon the delta session and request a full image from the server rather than attempting to apply a patch to a state it wasn't built for.

## Recovery: bootloader state machine and health checks

A slot switch completing and the new firmware booting is not the same as the update having succeeded - a new image can boot far enough to pass the bootloader's checks and still be broken in ways only visible after full initialization (a driver that panics, a comms daemon that crashes, a network stack that never comes up).

The standard pattern uses a bootloader-managed state machine backed by a hardware watchdog:

| State | Trigger | Next state | Bootloader/system action |
|---|---|---|---|
| Active | New image written and verified into Slot B | Pending-verify | Set flags: boot target = B, upgrade-available = 1, bootcount = 0 |
| Pending-verify | Reboot | Booting | Increment bootcount, hand control to Slot B |
| Booting | Boot succeeds and post-boot health checks pass | Committed | Slot B becomes the permanent active slot; clear upgrade-available |
| Booting | Watchdog fires, or bootcount exceeds a max-retry threshold | Rollback | Restore flags: boot target = A; clear upgrade-available |
| Rollback | Reboot | Active | Boots from the known-good Slot A |

The hardware watchdog is initialized early in boot. If the new image hangs or panics before it reaches the point of periodically resetting ("kicking") the watchdog, the timer expires and forces a hard reset. If the device cycles through this without ever reaching the commit step more than a configured retry limit, the bootloader gives up on the new image and reverts the boot target - automatically, without needing any external signal.

**Post-boot health checks** that actually determine "committed" status typically combine: system-service checks (did expected processes/services actually reach a running state), network sanity (can the device reach its OTA backend and complete a TLS handshake - a network stack regression that prevents this also prevents reporting success, so it has to trigger rollback rather than silently sitting broken), and hardware self-tests (can critical sensors and the secure element/key storage still be reached over their buses).

**RFC 9019 (SUIT - Software Updates for Internet of Things)** is the IETF standard specifically aimed at this class of resource-constrained device, explicitly scoped down to "Class 1" devices per RFC 7228 (roughly 10 KiB RAM, 100 KiB flash) - well below what a Linux-class A/B framework assumes. SUIT manifests are CBOR-encoded and cryptographically bound via COSE, structured as a sequence of commands a lightweight interpreter on the device executes: check component identifiers (vendor/class ID), check the declared version against the device's current version (the anti-rollback check), verify the target storage's hash, write the payload, then verify and hand off control. A companion extension (SUIT report) defines a compact CBOR status format so a device that fails or rolls back can report exactly which manifest command failed and why (hash mismatch, flash erase error, communication timeout) - useful for fleet-wide failure diagnosis rather than a bare "update failed."

## Sources

CRA Regulation (EU) 2024/2847, Annex I Part I point 2(c) and Part II points 7-8 - see `cra/essential-requirements.md` and `primary-sources/`. The Update Framework (TUF) specification (theupdateframework.io). Uptane Standard for Design and Implementation (uptane.org). RFC 9019 (A Firmware Update Architecture for Internet of Things) and the SUIT manifest CBOR/COSE draft specification. RAUC, Mender, and SWUpdate project documentation. MCUboot documentation (swap vs. direct-XIP). bsdiff, casync, and libostree/OSTree project documentation.
