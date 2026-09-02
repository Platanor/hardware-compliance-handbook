# SBOM implementation for embedded and IoT firmware

This is a technical reference for building and maintaining a software bill of materials (SBOM) on embedded and IoT firmware specifically. It assumes you already know *why* an SBOM is required - that's covered in `cra/essential-requirements.md` (Annex I, Part II, point 1). This page is about how to actually produce one when your build target is a cross-compiled, statically linked firmware image rather than a container or a server application with a package manifest.

## CycloneDX vs SPDX for firmware

Two formats cover almost all real-world embedded SBOM work: SPDX (Linux Foundation, standardized as ISO/IEC 5962:2021) and CycloneDX (OWASP).

SPDX moved from a single-document model in 2.2/2.3 to a graph-based, profile-driven model in SPDX 3.0. The 3.0 architecture splits metadata into separate profiles - Core, Software, Security, Build, AI, Dataset, Licensing, and Hardware - which lets you model precise relationships between a build process and the resulting binary. Its main practical advantage in embedded work is native build-system support: recent Yocto Project releases can emit SPDX documents directly from BitBake without a separate scanning step, and Zephyr RTOS ships a built-in `west spdx` command that generates an SPDX document set (app, kernel, build environment, module dependencies) from a normal build.

CycloneDX was built with operational security and vulnerability management as the primary use case. Version 1.6 added a `device` component type (not a `hardware` type - that's a common misreading of the spec), which lets a single CycloneDX document describe both the software running on a board and physical characteristics of the board itself: SoC model, PCB revision, a crypto co-processor, a radio module's own firmware. This makes CycloneDX the practical choice when you need a hardware bill of materials (HBOM) alongside the software one. CycloneDX also has native VEX (Vulnerability Exploitability eXchange) support built into the schema, which matters for suppressing false-positive CVE alerts (see below).

**Regulatory baseline:** BSI's technical guideline TR-03183-2 (v2.1.0, published 2025-08-20) - the German federal reference most CRA-facing SBOM discussions cite - accepts CycloneDX 1.6+ or SPDX 3.0.1+ and adds a recommended field mapping between the two. Older versions (CycloneDX 1.4/1.5, SPDX 2.2/2.3) fall outside that baseline. This is BSI guidance, not a CRA text requirement - the CRA itself doesn't mandate a specific SBOM format or version.

**Build-system support, as it actually stands today:**

| Build system | What ships by default | What you have to opt into |
|---|---|---|
| Yocto Project (Scarthgap, 5.0 LTS) | SPDX 2.2 via `create-spdx.bbclass` | SPDX 3.0.1 via `create-spdx-3.0.bbclass`, not the default class on this release |
| Yocto Project (Styhead, 5.1) | SPDX 3.0 became the default `create-spdx` output | - |
| Zephyr RTOS | `west spdx` generates SPDX 2.3 for app/kernel/build/modules | Doesn't cover sysbuild targets (bootloader, TF-M) cleanly as of 2026 |
| Buildroot | `make legal-info` (license/manifest CSV, not a full SBOM) | CycloneDX output via the `cyclonedx-buildroot` companion tool, or a `generate-cyclonedx.py`-style script some teams run against `legal-info` output - check your Buildroot version for what's actually integrated upstream vs. what still needs to be run as a separate step |

Don't take "Yocto generates SPDX natively" to mean "Yocto generates SPDX 3.0.1 by default" - on the current LTS (Scarthgap) the default is still 2.2, and you have to explicitly switch the inherited class to get 3.0.1 output.

A common practical pattern: generate SPDX during the build (because the build system already has the dependency graph), then convert to CycloneDX for feeding into a vulnerability-management platform like OWASP Dependency-Track, which has stronger CycloneDX-native tooling.

## Why embedded SBOM generation is harder than it looks

Server-side SCA tools assume an explicit package manifest (npm's `package.json`, Python's `requirements.txt`). Firmware doesn't give you that, for three structural reasons:

**Static linking and aggressive dead-code stripping.** Most RTOS and bare-metal firmware compiles to a single monolithic binary. Linker flags like `-ffunction-sections -fdata-sections -Wl,--gc-sections` remove unused sections, and symbol tables are typically stripped from production images. The textual and manifest-level markers a source-level scanner relies on are gone from the final artifact.

**Closed vendor blobs.** Firmware almost always integrates silicon-vendor code you didn't write and can't see into: BSPs, HAL libraries, precompiled radio-stack firmware for Wi-Fi/BLE/Zigbee. These ship as compiled object archives (`.a`, `.o`) with no visible source and no dependency declaration. A build-system scanner can record that `libvendor_wifi.a` exists; it can't tell you that vendor statically linked an old copy of lwIP or mbedTLS inside it.

**Cross-compilation reshaping the binary.** Cross-compilers (`arm-none-eabi-gcc`, `riscv64-unknown-elf-gcc`) at `-Os`/`-O3`, with inlining and target-specific instruction scheduling, produce a binary profile that looks nothing like the source tree it came from - which undermines signature-based binary scanners that expect recognizable code shapes.

Two complementary technique categories address this:

**Build-integrated / source-level SCA** - tools that run inside the build pipeline itself (Yocto's `create-spdx`, Zephyr's `west spdx`, or general-purpose scanners like Syft/cdxgen pointed at a source tree). These are precise for what they can see, but blind to the contents of closed vendor blobs, and prone to false positives in C/C++ trees where a `.c` file's presence in the repo doesn't guarantee it survived `#ifdef` conditionals and linker garbage collection into the final image.

**Binary composition analysis (BCA)** - tools that reverse-engineer the compiled image directly (open source: EMBA, cve-bin-tool; commercial: several firmware-security platforms). They unpack filesystems and ELF structures, and match string tables, constants, or function signatures against known open-source library fingerprints. Their weakness is the mirror image of the first category: stripped symbol tables and `-Os` optimization degrade signature matching, producing both false positives (wrong version match) and false negatives (missed statically-linked library).

In practice, a two-phase pipeline is the common approach: build-integrated generation produces an accurate SBOM for your own source and system packages, then a BCA pass over the final compiled image tries to surface what's hiding inside closed vendor blobs. Treat BCA output as a lead to investigate, not a fact to publish as-is - its error rate is meaningfully higher than build-integrated output.

## Direct vs. transitive dependency depth

CRA Annex I, Part II, point 1 requires the SBOM to cover "at least direct dependencies" - that's the regulatory floor, not a recommended stopping point.

The engineering argument for going deeper than direct dependencies: a high-level component - an IoT SDK, an MQTT client - rarely implements cryptography or networking itself. It pulls in a TLS stack (mbedTLS, wolfSSL) or a network stack (lwIP) transitively. If a vulnerability lands in that transitive library, a direct-dependency-only SBOM can't tell an automated system whether a given firmware revision is affected. Article 14's 24-hour initial-notification window for actively exploited vulnerabilities (from 11 September 2026, per `cra/essential-requirements.md`) makes that gap costly - manually reverse-engineering whether a transitive library is present, on a deadline measured in hours, is not a workable process.

The cost of going deeper: transitive graphs expand fast, and false-positive volume expands with them - a transitive component can appear in the source tree while being fully dead-code-eliminated from the shipped binary, which produces alerts against libraries that were never actually compiled in.

A workable split many teams land on:
- An external-facing SBOM (CycloneDX or SPDX) that satisfies the Annex I Part II point 1 floor with direct dependencies documented.
- An internal, fuller transitive dependency graph - loaded into a monitoring platform like OWASP Dependency-Track - used for continuous CVE monitoring and for meeting Article 14's response-time requirements.

## Matching a component to a CVE: why it's noisier than it should be

Mapping an identified component to a known vulnerability is one of the weaker links in embedded SCA, for two structural reasons.

**CPE vs. PURL.** NVD's legacy identifier, CPE 2.3, is built on free-text vendor/product naming with no central registry. In C/C++ embedded work, the same library can appear under several different vendor strings depending on who documented it, which causes both missed matches (name doesn't line up) and wrong matches (unrelated project sharing a name). PURL (`pkg:type/namespace/name@version`) is a stricter, more machine-reliable scheme, but C/C++ code vendored directly into a repo without a package manager often has no clean PURL to generate, which pushes scanners back onto CPE-style heuristic matching.

**Vendor backports.** Embedded Linux distributions rarely bump a library to a new major version mid-lifecycle, because of ABI/API breakage risk. Instead they backport a specific fix onto an older version string. NVD's advisory might say "all versions before 5.10.125 are vulnerable"; a scanner reading a manifest that says "5.10.120" flags it, even if the specific fix was already backported by the distro. This is a systemic source of false positives in embedded SCA, not an edge case.

**VEX as the correction mechanism.** VEX lets you publish a machine-readable statement that a specific CVE doesn't apply to your product, with a documented reason instead of a bare assertion. CycloneDX's own built-in VEX vocabulary defines justification values including `code_not_present` (the vulnerable code was stripped or tree-shaken at compile time), `code_not_reachable` (the vulnerable function is present but never invoked at runtime), and `protected_by_mitigating_control` (a documented compensating fix, such as a local backport, neutralizes it without a version bump). CSAF 2.0's own VEX justification enum covers the same ground with different, non-interchangeable names - see `technical/vulnerability-management.md` for the CSAF-specific list. The two formats are not wire-compatible, so pick one per artifact rather than mixing terminology. Without VEX in either form, every CVE match sits in a queue as an unresolved alert regardless of whether it's real.

Two things worth being explicit about here: there's no equivalent to npm or crates.io for C/C++, so PURL-to-CPE mapping quality varies by tool vendor rather than being standardized; and automated reachability analysis - determining whether a vulnerable function can actually be called - works reasonably well for managed languages (Java, Go) but is still immature for statically-linked C/C++ binaries, where function pointers, interrupts, and inlining make call-graph analysis unreliable.

## Keeping the SBOM current: build cadence, signing, multi-SKU

**Per-build vs. per-release.** A reasonable cadence separates the two: generate a disposable SBOM on every CI build to run automated security gates (block the build if a newly-added dependency carries a known-critical CVE or a disallowed license), and generate the canonical, signed SBOM only for release builds that actually ship via OTA.

**Signing.** Signing the SBOM alongside the firmware image - for example with `cosign sign-blob` (Sigstore) - ties the inventory to the specific signed artifact it describes, so a device's SBOM can't be substituted independently of the firmware it claims to describe.

**Multi-SKU products.** A single firmware codebase that targets multiple hardware variants (say, a cellular SKU and a Wi-Fi-only SKU) should not share one SBOM. `Kconfig` flags and `#ifdef` conditionals change which code actually ends up in each variant's binary, so a generic SBOM either overstates or understates what's really in a given device. The practical fix is generating a separate SBOM per build target (e.g. `MACHINE=sku-cellular` vs `MACHINE=sku-wifi` in Yocto, producing distinct output files per machine), and, where you're also tracking hardware composition, linking the SBOM to its corresponding HBOM entry (hardware SKU as parent, firmware as a `firmware`-type child component in CycloneDX terms).

## Sources

CRA Regulation (EU) 2024/2847, Annex I Part II point 1 (SBOM requirement) and Article 14 (vulnerability reporting timelines) - see `cra/essential-requirements.md` and `primary-sources/` for verified text. BSI TR-03183-2 v2.1.0 (2025-08-20). CycloneDX specification v1.6 (OWASP). SPDX 3.0.1 specification (Linux Foundation / ISO/IEC 5962:2021). Yocto Project documentation (Scarthgap 5.0 LTS and Styhead 5.1 release notes). Zephyr Project `west spdx` documentation. Buildroot `legal-info` documentation and the `cyclonedx-buildroot` project.
