# Device identity architecture for embedded and IoT

This is a technical reference on device identity - hardware roots of trust, IEEE 802.1AR, and factory provisioning. For the regulatory framing (what CRA does and doesn't require, and the RED caveat most CRA-focused writing misses), see the blog article `device-identity-iot-cra`; this page assumes that context and goes deeper on the engineering side.

## What device identity actually requires, precisely

Device identity is cross-cutting: it's the most defensible engineering answer to CRA Annex I, Part I, point 2(d), and it overlaps with 2(b) wherever "secure by default" gets implemented as a unique per-device credential rather than a shared one.

Point 2(d)'s exact text: "ensure protection from unauthorised access by appropriate control mechanisms, including but not limited to authentication, identity or access management systems, and report on possible unauthorised access." Two things worth keeping in view when using this to justify an architecture decision, not just when reading the regulation for the first time: the whole point is conditioned on "the cybersecurity risk assessment referred to in Article 13(2) and where applicable" - it's a risk-based obligation to assess and justify, not a fixed checklist - and the trailing clause requires detecting and reporting unauthorised access attempts, not just blocking them, which has implications for what a device needs to log and surface to a backend.

Annex I applies from 11 December 2027. If a product is internet-connected radio equipment, RED Article 3(3)(d) - in force since 1 August 2025 via Delegated Regulation (EU) 2022/30 - already reaches default-password and access-control practices through the harmonised standard EN 18031-1. A device identity architecture built to satisfy CRA's 2027 deadline should not assume there's no earlier deadline in play.

## Hardware roots of trust for identity

The credential's value depends entirely on where the private key lives and whether it can be extracted. Four architectural options cover most real designs.

**Secure elements (SE).** Discrete crypto co-processors - Microchip's ATECC608 family, NXP EdgeLock SE050, Infineon OPTIGA Trust M - generate asymmetric key pairs (typically ECDSA on NIST P-256/secp256r1) inside an isolated crypto boundary; the private key is never readable from outside the chip. The host MCU talks to the SE over I2C or SPI using a vendor library (CryptoAuthLib, Optiga Host Library) or APDU-style commands. These parts are built to resist side-channel and physical extraction attacks and draw very little standby current, which matters for battery-powered nodes. The tradeoff is limited secure NVM - typically low single-digit kilobytes to around 10 KB, or a fixed number of key slots - which is why compressed X.509 certificate formats exist specifically to fit a certificate into that space.

**TPM 2.0.** The TCG/ISO/IEC 11889 standard is the default on servers, PCs, and higher-end edge gateways, anchored by a manufacturer-provisioned Endorsement Key and Endorsement Certificate. Adoption on constrained embedded and MCU-class IoT hardware is low, for a concrete reason rather than just unfamiliarity: the standard TCG Software Stack (TSS2, with its FAPI/ESAPI/SYS abstraction layers) targets a full OS (Linux/Windows), not bare-metal or RTOS firmware, and pulling it in requires either that OS or a lightweight alternative stack such as wolfTPM. TPM also draws continuous power and costs more per unit than an SE, which rules it out for small battery-powered sensors even where the software fit isn't the blocker.

**Physically unclonable functions (PUF).** SRAM-PUF is the common implementation: powering an SRAM array produces a device-specific, largely-repeatable pattern of 0/1 states driven by microscopic threshold-voltage variation between transistors, unique to that specific die. The key property is that nothing is stored in nonvolatile memory in the powered-off state - there's no fuse or NVM cell to read out with microscopy or other physical inspection while the device is off. The practical complication is that the raw response isn't perfectly stable across temperature, supply noise, and aging, so a fuzzy extractor (built on error-correcting codes like BCH or Reed-Solomon, using accompanying "helper data") is needed to reconstruct the same key reliably on every boot.

**TCG DICE.** DICE gives MCUs without a discrete crypto chip a way to derive identity from the boot process itself. A Unique Device Secret (UDS) sits in OTP or protected NVM, gated by a hardware latch that cuts off read access after the first boot stage runs. At reset, the ROM measures (hashes) the first mutable code stage to get a value TCI, then derives a Compound Device Identifier as `CDI = HMAC(UDS, Hash(TCI))` (per the TCG DICE layering model - implementations may compose this differently, but the pattern is fixed: each layer's CDI feeds the next as its effective UDS, `CDI_next = HMAC(CDI_current, TCI_next)`). The UDS itself is then locked out until the next full reset. Long-lived (DeviceID) and short-lived (Alias) key pairs are derived from CDI, and the CDI value itself is cleared from RAM before handing off to the next stage. The property that matters: any change to the measured firmware produces a different TCI, therefore a different CDI, therefore different derived keys - a modified image cryptographically loses access to the legitimate device identity rather than just failing a separate integrity check.

| | Secure element | TPM 2.0 | PUF (SRAM) | TCG DICE |
|---|---|---|---|---|
| Typical BOM cost | Low-moderate | Moderate-high | Low (built into SoC) | Minimal (uses existing OTP/ROM) |
| Software stack complexity | Low (vendor C library) | High (TSS2, or wolfTPM for RTOS) | Moderate (fuzzy extractor) | Moderate (bootloader architecture) |
| Resource footprint | Very low | High | Low (RAM for helper data) | Very low |
| Key exists in NVM when powered off | Yes (in isolated crypto boundary) | Yes (in TPM's protected storage) | No | Yes, as UDS (access-gated after boot) |
| Bus/interface | I2C, SPI, single-wire | SPI, I2C, LPC | Internal to die | Internal registers/OTP |

## IEEE 802.1AR: IDevID and LDevID

IEEE 802.1AR formalizes device identity as X.509 v3 certificates and splits them into two classes with different lifecycles and issuers.

**IDevID** (Initial Device Identifier) is provisioned at the factory, signed by the manufacturer's own CA, and meant to be immutable for the device's life - it survives a factory reset. Its `notAfter` field is conventionally set to `99991231235959Z` (year 9999) to signal it isn't meant to expire on a normal schedule. It's the credential used for zero-touch onboarding flows: BRSKI (RFC 8995), FIDO Device Onboard, or LwM2M bootstrap.

**LDevID** (Locally-significant Device Identifier) is issued later by the operator's own PKI, after the device has proven itself via its IDevID. It's scoped to the deploying organization, has a limited validity period tied to that organization's policy, gets rotated through protocols like EST (RFC 7030) or CMP, and is deliberately wiped on factory reset. It's what a device presents for 802.1X/EAP-TLS network access or mTLS to operational backends day to day.

| | IDevID | LDevID |
|---|---|---|
| Issued by | Manufacturer/OEM CA | Operator's internal PKI |
| Storage | Hardware-protected (SE, TPM, OTP) | Protected or standard flash/NVM |
| Validity | Effectively unbounded | Bounded by operator policy |
| Survives factory reset | Yes | No, purged |
| Used for | Zero-touch onboarding (BRSKI, FDO, bootstrap) | 802.1X, mTLS, day-to-day operational API access |

Certificate profile notes that matter in practice: the `Subject` needs a `serialNumber` (OID 2.5.4.5) uniquely identifying the physical unit, and the SAN typically carries a `HardwareModuleName` or a `ProductInstanceURI`-style `OtherName`. Elliptic curve keys (secp256r1/P-256 at minimum) are the norm given constrained-device constraints.

Adoption is uneven by market segment. It's close to a baseline requirement in enterprise networking gear (routers, switches), industrial automation (PROFINET-aligned equipment), and professional edge hardware, where vendors already run their own PKI at scale. In consumer/mass-market IoT it's rare - the economics of running a manufacturing PKI, plus the lack of a standard ownership-transfer mechanism for smaller vendors, tend to push those product lines toward simpler static-token or PSK-based schemes instead. That gap is exactly what makes device identity a real differentiator on a security-conscious product, not just a compliance checkbox: a fleet running static per-model or shared credentials is the pattern behind most large-scale IoT compromises, and it's a gap a competitor without hardware-backed identity can't close without a hardware or manufacturing-process change.

## Factory provisioning at scale

Two models exist for getting a key pair onto a device during manufacturing.

**Key injection.** An external provisioning system generates the key pair and writes it into the device over a programming interface (SWD/JTAG, UART). This is weaker by construction: the private key exists outside the chip at least briefly, transits a physical test-fixture connection, and typically passes through the memory of whatever provisioning utility drives that fixture.

**On-chip generation.** The secure element or DICE-capable chip generates its own key pair internally using its hardware TRNG. The private key never leaves the protected boundary; the device exports only the public key or a CSR. This is the de facto standard for anything claiming genuine hardware-backed identity, precisely because it removes the injection step's exposure window.

A useful reference pattern for on-chip generation at contract-manufacturer scale is the HSM-mediated provisioning flow several secure element vendors offer (Microchip's Trust Platform tooling is a documented public example): the customer defines a key-slot and access-policy configuration using vendor tooling, receives that configuration back as a package encrypted to a specific factory-floor HSM's public key, the factory HSM handles CSR generation and gets it signed by the customer's own CA, and finally programs, provisions, and irreversibly locks the chip's configuration zone - after which the slot layout can't be altered. The point of routing everything through an HSM at the factory, rather than a general-purpose test controller, is that the private key material and the locking operation both stay inside hardware designed specifically not to leak either.

**Where this goes wrong**, independent of which model is used:

- **A compromised factory HSM or line operator**, if control is obtained before the locking step runs, can sign unauthorized firmware or provision "ghost" units with valid manufacturer certificates beyond the ordered quantity - overproduction that's cryptographically indistinguishable from the legitimate run.
- **The window before locking** is the highest-risk moment structurally: if debug interfaces on the test fixture or the target MCU are still live between power-on and the lock command, that's an opportunity to substitute a public key or intercept the provisioning bus.
- **An over-permissive link to the customer's own PKI** - an intermediate CA that signs on request without a hard cap tied to the ordered unit count - can let a factory issue more valid certificates than physical units shipped, without any single step looking obviously wrong in isolation.

## "Secure by default" credentials are not device identity

A recurring engineering mistake is treating a unique-per-device static password or symmetric pre-shared key as equivalent to device identity, because it satisfies the narrow "no shared default credential" reading of secure-by-default requirements. It's a materially weaker property.

| | Unique static credential | Hardware-anchored asymmetric identity |
|---|---|---|
| Typical form | Per-device password or symmetric PSK | Key pair in hardware RoT, signed by a CA |
| Exposure on bus sniffing | Weak - the secret itself crosses the wire or gets compared in the clear | Strong - only a signature crosses the wire, never the private key |
| Non-repudiation | None - a shared secret is known to both sides | Full - only the device holds the private key |
| Supports remote attestation | No - not bound to firmware state | Yes, where paired with DICE/TPM measurement |
| Backend scaling | Needs a database of every device's secret | Needs only the root CA's public key |

The practical consequence: a symmetric secret leaking from one device (via flash dump, bus sniff, or firmware extraction) is a credential-theft event scoped to that unit's secret, but if that secret was derived predictably or shared across a batch, it can scale to the whole batch. An extracted private key from a hardware-anchored identity, by contrast, compromises exactly one device and can be revoked without touching any other unit's trust chain.

## Retrofitting mistakes worth naming explicitly

Three failure patterns show up repeatedly when identity gets added to a product line that wasn't designed with it:

**Private keys in unprotected flash.** Generating the key pair in software and writing the private half to ordinary MCU flash/EEPROM makes it recoverable via JTAG, a voltage-glitch attack against read protection, or a buffer overflow in application firmware. It's software-scoped identity, not hardware-scoped, regardless of how the certificate is formatted.

**A single global key across the whole product line.** Encrypting or deriving device credentials from one symmetric master key hardcoded into the firmware means reverse-engineering one binary compromises every unit of that product ever shipped. This is the direct fleet-wide analogue of the shared-firmware-signing-key problem, but for identity rather than boot verification.

**No revocation path.** Provisioning certificates without a working renewal or revocation mechanism (CRL/OCSP, or an equivalent short-lived-certificate rotation scheme) means a single compromised intermediate CA or leaked device key can't be selectively blocked - the operational choice becomes disabling trust for the whole fleet or accepting the compromised unit.

## Migrating a mixed fleet

Where some units in the field have hardware-backed identity and older units don't, two patterns handle the split without forcing a hard cutover:

**Trust domain segregation.** New devices with an IDevID authenticate to the primary backend and get full operational API access. Legacy devices route through a separate, more restricted gateway - scoped tokens, IP allowlisting, network isolation (a dedicated VLAN) - rather than being granted the same trust level on weaker evidence.

**Software-emulated DICE on legacy OTP.** If the legacy MCU lacks a discrete secure element but has OTP and read-protection support, a new bootloader (delivered via an OTA update) can generate a UDS into OTP and then permanently disable external interface access to that OTP region, giving the device a DICE-style `CDI = HMAC(UDS, Hash(firmware))` binding going forward - weaker than a part designed for this from the start, since the OTP write happens post-manufacture rather than in a controlled factory environment, but a real improvement over no hardware binding at all.

**EST-based dynamic bootstrap.** For devices with no IDevID at all, a one-time enrollment on a controlled network - generate a key pair in flash, submit a CSR over EST (RFC 7030) to get an operational LDevID - moves a fleet onto a standard X.509 identity format. This does not add hardware-backed anti-cloning protection (the key is still software-extractable), but it does get legacy devices onto the same certificate-based authentication model as new hardware, which is often the more urgent operational problem.

## Sources

CRA Regulation (EU) 2024/2847, Annex I Part I point 2(b) and 2(d) - see `cra/essential-requirements.md`, `primary-sources/`, and the blog article `device-identity-iot-cra` for the verified regulatory text and the RED Article 3(3)(d)/EN 18031-1 caveat. IEEE 802.1AR-2018 (Secure Device Identity). TCG DICE architecture documents and TCG Hardware Requirements for a Device Identifier Composition Engine. NIST SP 800-63 (explicitly scoped to human/subscriber identity, not machine-to-machine or IoT) and NISTIR 8259 (the IoT-relevant NIST reference). RFC 8995 (BRSKI), RFC 7030 (EST). Vendor documentation: Microchip ATECC608/Trust Platform, NXP EdgeLock SE050, Infineon OPTIGA Trust M.
