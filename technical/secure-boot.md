# Secure boot architecture and implementation gaps

This is a technical reference on secure boot implementation across embedded and IoT platforms. It goes deeper than the beginner-level blog article on the same topic - assumes you already know what a chain of trust is and why CRA Annex I, Part I, point 2(f) (protection of the integrity of data and system components) expects one. This page is about where real implementations diverge from the textbook description, and where that divergence actually gets exploited.

The vendor-marketing version of secure boot - "cryptographic signature check before handing off to the next stage" - hides real differences in memory layout, crypto primitives, isolation, and manifest format between platforms. Those differences are where implementation bugs live.

## Two reference architectures

**UEFI Secure Boot** targets higher-end SoCs (x86_64, ARM64/AArch64). Verification is based on X.509 certificates and the PE/COFF binary format, with a key hierarchy stored in NVRAM: `PK` (Platform Key), `KEK` (Key Exchange Key), `db` (allowed signatures), `dbx` (revoked signatures). Verification runs during the DXE/BDS boot phases.

**ARM Trusted Board Boot Requirements (TBBR)**, used across Cortex-A and ARMv8-M/v9-M (TrustZone), defines a stricter staged chain of trust:

- **BL1** - immutable BootROM code, first to run after reset.
- **BL2** - Trusted Boot Firmware, verified against a Root of Trust public key hash (`RotPK`) burned into OTP/eFuse.
- **BL31** (EL3 runtime) / **BL32** (Secure OS / TEE) - run inside the isolated Secure World.
- **BL33** - non-secure firmware (U-Boot, OS kernel), runs in the Normal World.

## Vendor implementations

Every silicon vendor adapts the same underlying idea to its own hardware blocks, and the differences matter for where things can go wrong.

**NXP - HAB and AHAB.** These are two different architectures for two different SoC generations, not one lineage: classic High Assurance Boot (HAB), on i.MX6/7-class parts, verifies images against a CAAM-based crypto block without a separate security co-processor. Advanced HAB (AHAB), on i.MX8-class parts, is architecturally different - a dedicated Security Controller (SECO) authenticates images while the System Control Unit (SCU) manages loading them from boot media, communicating over an internal message unit. Verification uses a Super Root Key (SRK) table, hashed into eFuse, and a Command Sequence File (CSF) built with NXP's Code Signing Tool that specifies what to authenticate and which keys to use.

**STMicroelectronics - SBSFU and TF-M.** On MCUs without TrustZone, trust is anchored in Option Bytes configuration: read-out protection (RDP Level 1/2), write protection (WRP), proprietary code protection (PCROP), and a hardware-locked Secure Area. X-CUBE-SBSFU verifies the application image before handing off control and manages secure OTA through dual-bank flash. On ARMv8-M parts (STM32L5, U5, H5), the same role is filled by TF-M combined with MCUboot.

**Nordic Semiconductor.** nRF52-series parts run MCUboot. By default MCUboot compiles the full public key directly into the bootloader's own flash image and exposes only its hash to the image manifest as a `KEYHASH` TLV entry - the key itself isn't in a separate hardware slot, it ships as part of the bootloader binary. A hardware-backed alternative (`MCUBOOT_HW_KEY`) exists, where only a key hash is provisioned to a target-specific secure location and the bootloader retrieves it through a target-implemented callback; on Nordic parts this is a design choice, not the out-of-the-box default, and where UICR is used for this it's one possible implementation of that callback, not a documented standard slot. Debug lockout goes through the APPROTECT register. Dual-core parts (nRF5340, nRF54-series) add a hardware crypto accelerator (CryptoCell-312 or CRACEN) with full TF-M support and hardware separation between the Application and Network cores via the System Protection Unit (SPU/IDAU).

**Espressif - Secure Boot V2 (ESP32-S2/S3/C3/C6/H2).** Verification is anchored in BootROM: at boot, the ROM reads a SHA-256 digest of the RSA-3072 (or ECDSA) public key from eFuse block 2. Up to three independent key slots (Keys #0-#2) can be provisioned, each with its own `KEY_DIGEST` and `KEY_REVOKE` eFuse bit, which lets a compromised signing key be permanently revoked in the field without revoking the others.

| | UEFI Secure Boot | ARM TBBR | NXP HAB / AHAB | ST SBSFU / TF-M | Nordic (nRF53/54) | Espressif SB V2 |
|---|---|---|---|---|---|---|
| Root of trust | NVRAM / flash root cert | BootROM + OTP hash (`RotPK`) | CAAM (HAB) or SECO/SCU + eFuse SRK table (AHAB) | BootROM/immutable flash + Option Bytes | BootROM/TF-M + key-in-bootloader-flash by default, optional hardware key hash via target-specific storage | BootROM + eFuse key digest |
| Typical algorithms | RSA-2048/4096, ECDSA P-256/384 | RSA-2048/4096, ECDSA P-256/384 | RSA-2048/4096, ECC P-256/384/521 | RSA-2048/3072, ECDSA P-256 | RSA-2048, ECDSA P-256, Ed25519 | RSA-3072, ECDSA P-256 |
| Manifest format | PE/COFF + Authenticode | Certificate chain (X.509 or custom) | CSF / container structure | TLV header + signature | MCUboot TLV header | Signature block + header |
| Memory isolation | SMM/MMU | SAU/IDAU, TrustZone NS/S | CSU, XRDC, SECO TCM vs. AP RAM | MPU, TrustZone, HDP/PCROP | SPU, TrustZone-M | Flash encryption, MPU, key vault |

## Anti-rollback: how it's built, and how it fails

Signature verification stops modified or unsigned code from running. It does nothing to stop a valid, vendor-signed *old* image with a known vulnerability from being reinstalled - a downgrade attack. The countermeasure is a monotonic version counter, typically held in OTP/eFuse (or a secure counter inside a TPM/secure element): the bootloader compares the new image's declared security version against the hardware counter, only proceeds if the image version is greater than or equal to it, and increments the hardware counter after a successful boot.

Hardware counters in OTP are commonly implemented as unary bit arrays, where each burned bit represents one version increment - version 0 to version 3 means burning bits in sequence: `00000000 → 00000001 → 00000011 → 00000111`. Because an eFuse bit physically cannot be un-burned, the counter can't be lowered at the hardware level.

Getting this wrong in practice tends to fail in a few specific ways:

**Counter exhaustion.** The eFuse bit budget for anti-rollback is fixed at silicon design time. If a product's patch cadence outpaces that budget, the counter saturates. If the bootloader then silently stops incrementing, rollback protection quietly stops working for every update after that point. If the bootloader instead enforces the comparison strictly, the device becomes unable to accept further updates at all.

**Non-atomic writes and power loss.** Programming an eFuse bit requires a specific voltage level held for a defined window. A brownout or sudden power loss during that window can leave the cell in an indeterminate state, which downstream read logic may interpret as either an ECC error or an unstable 0/1 read on every subsequent boot.

**Ordering bugs.** A serious design flaw shows up when the bootloader burns the new anti-rollback value into eFuse *before* confirming the new image actually boots successfully. If the new image turns out to be broken, the device can't fall back to the previous known-good version, because its version is now below the already-burned counter. The correct pattern is deferred commitment: write the update to the inactive bank, and only increment the hardware counter after the new image has completed a successful first-boot self-test.

**Register-width bugs in the revocation code itself.** Software bugs in the bootloader can silently defeat the hardware protection regardless of how correctly the silicon itself works. A documented example is Espressif's `esp_ota_revoke_secure_boot_public_key()` (tracked as ESP-IDF issue IDFGH-11749): the function accessed eFuse key-digest registers through a `uint8_t*` pointer, but ESP32's eFuse registers only support 32-bit-aligned access. The 8-bit reads always returned zero, so the function always concluded the key slot was empty and silently failed to revoke it - leaving devices that believed they'd revoked a compromised key still trusting it.

## Where real systems break trust anyway

A device can pass formal secure-boot conformance testing and still ship with gaps that undo it. The pattern in published hardware research is consistent: attackers target implementation edge cases and boundary conditions, not the underlying RSA/ECC math.

**Debug interfaces disabled in software instead of fused off.** The common mistake is disabling JTAG/SWD by writing a configuration register during bootloader execution, rather than permanently blowing a fuse. That leaves a real window, from reset to the instruction that performs the disable, during which a precisely timed voltage or clock fault injection can skip or corrupt that instruction and leave the debug port live. Published attacks against Nordic APPROTECT follow exactly this pattern - the protection is applied during early boot, and a correctly timed glitch in that window can prevent it from ever engaging. STM32 RDP Level 1 fails a related but distinct way, worth not conflating with the timing-window class: RDP1 is *designed* to still allow arbitrary code execution from SRAM over the debug port even though it blocks direct flash reads, no glitch required for that part - an attacker loads a small dumper routine into SRAM via SWD and has it read flash from the inside (code executing on-chip was never subject to the external-read restriction) and shift the bytes back out over a peripheral. Where fault injection *does* come in for RDP is a separate attack: glitching the mass-erase that's supposed to run when downgrading protection level, so flash contents survive a level drop that's meant to wipe them first. The only interface-level protection that actually removes the physical connection for either class of gap is a hardware fuse - STM32 RDP Level 2 or ESP32's `JTAG_DISABLE` eFuse bit - burned in production, not toggled by firmware at runtime.

**Unsigned recovery paths.** An unauthenticated recovery or USB-boot mode undermines secure boot regardless of how solid the main boot path is. The clearest documented case is Fusée Gelée (CVE-2018-6242) in NVIDIA Tegra X1's BootROM USB recovery mode (RCM): the ROM's USB control-endpoint handler read an attacker-controlled length field and passed it to a DMA copy without bounds-checking it, overflowing a fixed-size buffer into the active stack before any signature check occurred. Because this happened in the data-reception path, ahead of verification, it gave full unsigned code execution at BootROM privilege. Because BootROM is mask-programmed at the fab, this could not be fixed with a firmware update - Nvidia had to ship a new silicon revision ("Mariko") to close it.

**Test keys or an incomplete chain.** Two recurring gaps in shipped products: leftover vendor SDK test keypairs left enabled in production builds (so anyone with the published test key can sign an accepted image), and a chain of trust that verifies stage 2 but stops there - stage 2 loads the OS kernel or main application with no further verification, or an external QSPI flash holding the root filesystem is left entirely unverified even though the code copied into internal SRAM is checked.

## Where the root of trust physically lives

The physical location of the root of trust drives cost, manufacturing complexity, and resistance to physical attack.

| | Immutable mask ROM | On-chip eFuse/OTP | External secure element/TPM | SRAM PUF |
|---|---|---|---|---|
| Fault-injection resistance | High (code is fixed) | Moderate (read-path is attackable) | Very high (hardware fault detectors) | High |
| Side-channel resistance | Not applicable | Moderate | Very high (masking/noise injection) | High |
| BOM cost impact | None (part of the SoC) | Minimal | High (extra chip) | Moderate (IP licensing) |
| Manufacturing step | None extra | Requires factory HSM-based fusing | Requires secure provisioning | Self-initializing |
| Key uniqueness | Shared across the whole SoC line | Unique per device (`RotPK` hash or device key) | Unique ID + hardware certificate | Unique per die |

A mask-ROM bug, as Fusée Gelée shows, can't be patched - only replaced with a new silicon revision. An external secure element (Microchip ATECC608, ST STSAFE-A110, NXP EdgeLock) adds real protection against invasive attacks, but also adds a new attack surface: the bus between MCU and secure element (I2C/SPI) needs its own encryption and session-key authentication, or it becomes the easiest way in.

## Secure boot vs. measured boot

These get conflated often enough that it's worth being precise. Secure boot is an enforcement mechanism: it answers "is this code allowed to run", and halts if a stage fails verification. Measured boot is a recording mechanism: it answers "what code and configuration actually ran", and does not stop execution even for unknown or modified code. Instead it hashes each loaded stage and extends that hash into a protected register (a TPM PCR, or via DICE - Device Identifier Composition Engine), using the standard extend operation `PCR_new = Hash(PCR_old || Measurement)`. A remote attestation server can later challenge the device and check whether the recorded measurements match a known-good state.

The gap measured boot closes: if an attacker has a legitimately signed but outdated or vulnerable bootloader (a "BlackLotus-style" scenario), secure boot verifies the signature and lets it run - it was never designed to know the image is old. Measured boot records exactly which version ran, so a remote verifier can catch it at attestation time even though local boot succeeded. It's also the only one of the two that can meaningfully cover configuration data and not just binary code.

NIST SP 800-193 (Platform Firmware Resiliency Guidelines) frames this as three separate pillars a firmware security architecture needs: protection (mechanisms keeping firmware in a state of integrity - what secure boot implements), detection (mechanisms for detecting when firmware has been corrupted or changed from an authorized state - what measured boot exemplifies, though 800-193's definition is broader than measured boot alone), and recovery. Systems expected to support remote attestation of device state - which CRA-aligned and IEC 62443 environments increasingly assume for critical equipment - need measured boot in addition to secure boot, not instead of it.

## Retrofitting secure boot onto an existing product

Retrofitting is a common real situation: a product already shipping, built on an MCU with no BootROM-level verification and no OTP/eFuse key storage. It's only possible if the part has at least minimal flash protection primitives (Option Bytes, write protection, an MPU).

The pattern is a "soft root of trust": a Stage 0 bootloader placed in the lowest flash sectors, holding the update-verification public key, with write protection enabled on that sector via Option Bytes and debug interfaces disabled through the same mechanism (RDP Level 2 or equivalent). Stage 0 verifies the main application image's signature and integrity before handing off control.

This is a materially weaker architecture than a clean-slate design, for reasons worth being explicit about rather than glossing over:

- **Option Byte glitching.** On many classic MCUs, protection-bit state is read from flash into core configuration registers on the reset edge. A precisely timed voltage glitch during that window can make the core read the protection bits as disabled, exposing the Stage 0 bootloader's flash sector to erase and rewrite over SWD.
- **No hardware anti-rollback.** Without eFuse, the version counter has to live in ordinary flash or an NVS structure. An attacker with physical board access can erase that sector directly, or mass-erase the flash, resetting the counter to zero and re-enabling old vulnerable firmware.
- **No runtime key isolation.** Without TrustZone or an MPU-isolated secure region, the verification public key (or symmetric keys) sits in general SRAM during bootloader execution - reachable by any buffer overflow in the application itself.

None of this makes retrofitting the wrong call - it's often the only option on hardware already in the field - but it needs to be evaluated with those specific residual risks in mind, not treated as equivalent to a hardware root of trust.

## Sources

CRA Regulation (EU) 2024/2847, Annex I Part I point 2(f) - see `cra/essential-requirements.md`, `primary-sources/`, and the blog article `what-is-secure-boot-iot-devices-cra` for the beginner-level walkthrough this page builds on. ARM Trusted Board Boot Requirements (TBBR) / Trusted Firmware-A documentation. NXP AHAB documentation (i.MX 8/8X security reference manuals, Code Signing Tool guides). STMicroelectronics X-CUBE-SBSFU and TF-M/STM32 documentation. Nordic Semiconductor nRF Connect SDK security documentation. Espressif ESP-IDF Secure Boot V2 documentation and GitHub issue IDFGH-11749 (`espressif/esp-idf#12851`). CVE-2018-6242 (Fusée Gelée) public disclosure and technical writeups. NIST SP 800-193, Platform Firmware Resiliency Guidelines.
