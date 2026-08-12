**Analysis of the Annex I essential cybersecurity requirements of the Cyber Resilience Act (EU 2024/2847)**

Regulation (EU) 2024/2847 on horizontal cybersecurity requirements for products with digital elements (Cyber Resilience Act, CRA) creates a new legal standard for manufacturers, importers, and distributors on the EU market. The core technical obligations, compliance with which is a mandatory precondition for CE marking and access to the EU internal market, are concentrated in Annex I of the regulation.

Annex I has a two-part structure. Part I governs the direct properties and architectural characteristics of the product with digital elements, embedding security-by-design and secure-by-default principles. Part II sets out requirements for the mandatory vulnerability-handling processes that a manufacturer must maintain continuously throughout the product's entire lifecycle.

**Legal layer, harmonised standards, and the state of the presumption of conformity as of mid-2026**

Under Article 27 of Regulation (EU) 2024/2847, meeting the Annex I essential requirements is legally made easier through the presumption-of-conformity mechanism. A manufacturer that applies harmonised standards whose references have been published in the Official Journal of the European Union (OJEU) is presumed to comply with the corresponding essential requirements of the regulation.

On 3 February 2025, the European Commission adopted standardisation request M/606, addressed to the European standardisation organisations CEN, CENELEC, and ETSI; in April 2025, those organisations formally accepted the request. The request tasks them with developing an extensive set of standards, with the horizontal prEN 40000-1-x series playing a central role, alongside specific vertical standards for particular product categories.

**Architecture of the harmonised standards under the CRA and their development status**

| **Standard type** | **Designation/series** | **Standardisation subject** | **Link to Annex I** | **Development status as of mid-2026** |
| --- | --- | --- | --- | --- |
| **Type A (Framework)** | **prEN 40000-1-2** | Cyber-resilience principles and risk-assessment methodology | General framework requirements, Part I, point 1 | Public enquiry closed, text finalisation underway |
| **Type B (Product-agnostic)** | **prEN 40000-1-3** | Vulnerability handling processes | Covers all 8 points of Annex I, Part II | Public enquiry closed, final draft in preparation |
| **Type B (Product-agnostic)** | **prEN 40000-1-4** | General technical security requirements for products | Technical points, Part I, points 2(a)–2(m) | In development by working groups |
| **Type C (Product-specific)** | **ETSI EN 304 6xx / EN 50765 / prEN 50770** | Specific requirements for particular categories (OS, network devices, OT, secure elements) | Detailed Part I and Part II requirements for the relevant product classes | Development status per standard not confirmed by a primary source (M/606 only gives deadlines, not the current draft status) — refer to the official ESO tracker, not this table |

**Legal status and standard-publication timelines**

The current (original) M/606 standardisation request timeline requires drafters to submit the two core horizontal standards (Type A/B — cyber-resilience principles and vulnerability handling, including prEN 40000-1-2 and prEN 40000-1-3) to the Commission by **30 August 2026**, the vertical product-specific standards (Type C) by **30 October 2026**, and the remaining horizontal standards by 30 October 2027.

In early July 2026, the European Commission published a **draft** amendment to the M/606 request that would push these two 2026 deadlines back by roughly two months (to around 31 October 2026 for Type A/B and 31 December 2026 for Type C). As of mid-2026, this amendment has not been formally adopted — the corresponding Commission implementing decision has not yet been published in the EU Official Journal, so the original dates (30 August/30 October 2026) remain in force until the amendment is formally approved. The amendment does not affect the 30 October 2027 deadline for the remaining horizontal standards. Importantly: shifting the standard-submission deadlines does not, in any way, change the regulation's own entry-into-force dates (notably 11 September 2026 and 11 December 2027).

A critical legal point is that a drafter submitting a draft standard to the European Commission does not give it legal effect. The presumption of conformity under Article 27 of the regulation only becomes active once a reference to the approved standard is officially published in the EU Official Journal (OJEU).

As of mid-2026, no harmonised standard for the CRA has been published in the EU Official Journal. Consequently, as of mid-2026 there is no legally operative presumption of conformity via the prEN 40000 series of standards. Engineering teams developing and preparing technical documentation are, for now, forced to rely on the available public drafts, along with related international standards such as ISO/IEC 29147, ISO/IEC 30111, IEC 62443, and the BSI TR-03183 guidance.

**Annex I Part I — requirements for the properties of products with digital elements**

Part I of Annex I sets mandatory requirements for the design, development, and manufacturing characteristics of products with digital elements. All technical decisions must be grounded in the results of a prior risk assessment.

**Point 1: general requirement for risk-based design**

This requirement obliges products with digital elements to be designed, manufactured, and supplied in such a way that they ensure an appropriate level of cybersecurity based on the risks. Absolute security is not required, but protective measures must be proportionate to the threats.

To meet this requirement, an engineer must integrate formal threat modelling directly into the system architecture before writing any code. The product's valuable assets, possible attack vectors, and potential consequences must be identified, with acceptable countermeasures documented in a structured risk assessment report (per Article 13(2) of the regulation).

In practice, this requires threat-modelling methodologies such as STRIDE, PASTA, or LINDDUN, using tools like OWASP Threat Dragon or IriusRisk. Risk documentation is kept as declarative files directly in the source code repository, following a Code-as-Documentation approach.

**Important caveat: the conditional nature of point 2 (applies to all sub-points 2(a)–2(m) below)**

Point 1 of Annex I Part I is unconditional. But the whole of point 2 opens with: "On the basis of the cybersecurity risk assessment referred to in Article 13(2) and where applicable, products with digital elements shall: …" This means each of the sub-points 2(a)–2(m) below is doubly conditional: on the manufacturer's own risk assessment, and on the "where applicable" criterion. The regulation does not mandate implementing every technical control in the matrix below as compulsory — it requires carrying out a risk assessment, choosing proportionate measures, and justifying the choice in the technical documentation (Annex VII). A manufacturer that has documented why a given control is not appropriate for its product is taking a position the regulation expressly allows. The phrasing below ("the engineer must…") describes the typical, most common engineering solution for meeting the requirement — not an unconditional mandate from the regulation itself.

**Point 2(a): absence of known exploitable vulnerabilities**

A product may not be placed on the market with known exploitable vulnerabilities. Important: Article 3(41) defines an "exploitable vulnerability" as one that "can potentially be effectively exploited by an attacker under practical operational conditions" — the regulation does **not** require a public PoC or published exploit code for a vulnerability to fall under this prohibition.

The engineer must set up scanning of the product's own source code and all third-party and open-source libraries at build time. If a component in use is found to have a fixable vulnerability (CVE) that is technically exploitable under realistic usage conditions for the product — regardless of whether a public exploit exists — the engineer must update the component, apply a patch, or prove and document, through reachability analysis, that the vulnerability cannot be exploited in this product.

A practical technical solution is implementing Software Composition Analysis (SCA) tools, such as Dependency-Check, Snyk, Trivy, or JFrog Xray. These tools are integrated into the CI/CD pipeline, with a rule blocking automatic builds if an unresolved high-risk CVE is found; a listing in the CISA KEV or EUVD catalogues raises priority, but is not the only criterion — a CVE without such a listing can still be "exploitable" within the meaning of Article 3(41) and must be remediated.

**Point 2(b): secure-by-default configuration and the ability to reset**

The product must ship with the strictest security settings "out of the box," and must have a simple, secure mechanism for restoring its original state. The regulation does not literally prohibit identical factory passwords in the text of Annex I — this is an established engineering practice for meeting the secure-by-default requirement (aligned, among other things, with ETSI EN 303 645), not a separate literal prohibition in the CRA's text. Exception: Annex I, Part I, point 2(b) expressly allows departing from this requirement "where otherwise agreed between manufacturer and business user" for a tailor-made product.

The engineer must fully remove hardcoded credentials from the source code. A first-boot setup wizard must be implemented that forces the user to set a unique, strong password on first use. All insecure or unused network services must be disabled by default. A software or hardware factory-reset procedure must also be provided.

Typical solutions include using algorithms to generate a unique password for each device (printed on the housing), enforcing a mandatory first-boot onboarding workflow, and handling interrupt signals from a physical reset button to trigger a secure-wipe procedure.

**Point 2(c): delivery of security updates and automatic updating**

The product must support fixing vulnerabilities through security updates. Automatic security updates must be enabled by default, but the user must be able to easily disable this (an opt-out mechanism).

The engineer must build a background update agent that, once deployed, connects to an update server and automatically downloads critical patches without operator intervention. A clearly visible toggle for switching updates to manual mode must be provided in the graphical, console, or web interface.

Technically, this is implemented using FOTA/OTA update agents (based on RAUC, SWUpdate, or Mender) with a dual (A/B) partition architecture to protect against write failures. The automatic-update configuration flag defaults to true, with the ability to change it via the user interface or API.

**Point 2(d): protection against unauthorised access and notification**

The product must restrict access to authenticated and authorised persons or systems only, through appropriate access-control mechanisms, and must record and report unauthorised access attempts.

The engineer must implement authentication checks on all exposed network and local interfaces and enforce least-privilege access separation. A notification subsystem must also be built that generates security events when repeated login failures or privilege-escalation attempts are detected.

Practical solutions include implementing OAuth 2.0, OpenID Connect, mutual mTLS authentication with hardware certificates, applying brute-force protection (Fail2ban, rate limiting), and feeding authentication events into logged PAM subsystem modules.

**Point 2(e): protection of data confidentiality**

Sensitive data stored or transmitted by the product (including configurations, session keys, personal data, and commands) must be protected against unauthorised reading through cryptographic means.

The engineer must fully eliminate the use of unencrypted network protocols and ensure local databases and system partitions are encrypted. Cryptographic keys must not be stored in source code or plain files.

The technical solution consists of encrypting communication channels via TLS 1.3, SSHv2, or IPsec. Local data is encrypted using AES-256-GCM or ChaCha20-Poly1305, with master encryption keys isolated inside Secure Element, TPM 2.0, or ARM TrustZone hardware modules.

**Point 2(f): protection of the integrity of data and system components**

The product must detect and block any attempt at unauthorised modification or corruption of code, configurations, and executable data.

The engineer must implement digital-signature verification at every stage of loading and executing software. Any unauthorised modification of the system image must halt the boot process or switch the device into an emergency-recovery mode.

In practice, this is achieved by implementing a Secure Boot chain of trust (based on UEFI Secure Boot or ARM Trusted Board Boot), real-time filesystem integrity verification modules (dm-verity on Linux), and SHA-256/HMAC checksums for configuration files.

**Point 2(g): minimisation of processed data**

The product must collect and process only the volume of data that is strictly necessary for its intended functional purpose.

The engineer must audit all telemetry fields, system logs, and user data, removing excessive collection of geolocation, device identifiers, or user actions. Temporary files and log files must be cleared automatically.

Technically, this is implemented through on-device data anonymisation modules (edge anonymisation), stripping personal data (PII) from telemetry packets before they are sent, and setting strict time-to-live (TTL) retention policies for temporary data structures.

**Point 2(h): protection of availability and resilience against DoS attacks**

The product must maintain its critical functions during request-flooding attempts or denial-of-service (DoS/DDoS) attacks.

The engineer must implement protection against exhaustion of system resources (memory, CPU time, file descriptors). Request-rate limiting must be implemented and priority given to critical processes.

Typical solutions include configuring hardware and software watchdog timers, applying rate-limiting algorithms (leaky bucket/token bucket), and enabling SYN cookies in the Linux kernel network stack (net.ipv4.tcp_syncookies = 1).

**Point 2(i): minimising negative impact on other systems**

The product must be designed so that, if compromised, its negative impact on other devices, network services, or the broader infrastructure is minimised.

The engineer must isolate software components from each other and from the external network using access-control systems with the minimum necessary privileges.

Practical solutions include containerising applications (Docker, podman), using isolated microVM runtime environments (Firecracker), enabling mandatory access-control systems (SELinux, AppArmor), and restricting network interaction through microsegmentation.

**Point 2(j): minimising the attack surface**

The product must expose the minimum attack surface necessary, including external interfaces, the codebase, and network services.

The engineer must remove debugging tools from the final firmware, disable unused physical interfaces, and remove unnecessary packages, libraries, and network daemons from the operating system.

In practice, this is implemented by physically disabling JTAG/UART debug ports (via eFuse blowing) before the device leaves the factory, building minimal OS images with the Yocto Project or Buildroot, using distroless containers, and closing all unknown network ports with a local firewall.

**Point 2(k): reducing the impact of compromise on the network**

The product must include mechanisms that, if it is compromised, prevent it from being used to automatically spread attacks to other nodes (for example, as part of a botnet).

The engineer must restrict the device's ability to initiate arbitrary outbound network traffic and rule out the possibility of executing arbitrary code from memory or local partitions.

Technically, this is achieved by configuring strict egress-filtering rules, allowing connections only to an explicit list of the manufacturer's domains, and enabling hardware memory-protection features: DEP/NX (no-execute bit), ASLR (address space layout randomisation), and the W^X (write XOR execute) principle.

**Point 2(l): recording and secure storage of security events**

The product must record and monitor internal activity relevant to security, including data access or configuration changes, **with a mechanism allowing the user to opt out of this logging** — a requirement expressly stated in the text of point 2(l), unlike protection of logs from tampering, which is good engineering practice but not a literal requirement of this point.

The engineer must configure audit-record generation for all critical security events, implement a mechanism for the user to disable such logging on request, and ensure records are sent immediately to a remote server or a secure local store inaccessible to a regular user or an attacker.

Solutions include configuring the auditd or syslog-ng subsystem to transmit logs over an encrypted TLS channel (RFC 5425), applying cryptographic log chaining to detect deleted entries, and storing logs on read-only filesystem partitions.

**Point 2(m): secure data erasure and decommissioning**

The product must let the user easily, securely, and permanently delete all personal data and settings, and must guarantee secure data handling when decommissioned or transferred to a new owner.

The engineer must build a function for fully wiping storage, or for rapidly destroying the keys used to encrypt that data, with no possibility of recovery.

In practice, this uses crypto-shredding (instantly wiping the master encryption keys for partitions stored in a secure element), along with low-level hardware memory-wipe commands (NVMe Sanitize, eMMC Erase, or blkdiscard).

**Annex I Part II — requirements for vulnerability handling processes**

Part II of Annex I governs the operational vulnerability-handling processes a manufacturer must maintain throughout the product's entire defined support period.

**Point 1: creating and keeping the software bill of materials (SBOM) up to date**

The manufacturer must identify and document all of a product's software components, including creating a detailed software bill of materials (SBOM) in a machine-readable format, covering at least direct dependencies.

The engineer must build automatic SBOM generation into the product's CI/CD build process. The generated SBOM is kept as part of the product's technical documentation and updated whenever the set of dependencies changes.

The technical solution uses SBOM-generation tools (Syft, CycloneDX CLI, cdxgen), exporting to the standard machine-readable CycloneDX or SPDX formats in JSON or XML. Storing and monitoring the SBOM is done in dedicated systems (Dependency-Track).

**Point 2: prompt vulnerability remediation and providing updates**

Discovered vulnerabilities must be remediated without condition and without undue delay, through developing and freely providing security updates or patches.

The engineer must set up continuous, automated monitoring for new CVEs across all components listed in the SBOM. When a vulnerability is found, an urgent task is created to update the component, run regression testing, and release a targeted fix.

Practical solutions include integrating the Dependency-Track platform with issue-tracking systems (Jira, GitLab Issues), where tickets with clear remediation deadlines are created automatically based on CVSS severity, and using dedicated patch branches in Git.

**Point 3: regular security testing and audits**

The manufacturer must carry out regular, effective testing and security checks of the product with digital elements throughout its lifecycle.

The engineer must build static and dynamic code analysis into the DevSecOps pipeline, and regularly subject the product to fuzz testing and third-party penetration testing.

In practice, this is achieved by integrating SAST scanners (SonarQube, Checkmarx), DAST (OWASP ZAP), and fuzzing tools (AFL++, Atheris) into the CI/CD process, and engaging accredited external labs for annual penetration testing.

**Point 4: public disclosure of fixed vulnerabilities**

After a security update is released, the manufacturer must publicly disclose information about fixed vulnerabilities, including their description, severity, impact assessment, and instructions for users on applying the patch. Annex I, Part II, point 4 provides an exception: in duly justified cases, where the manufacturer considers that the risks of disclosure outweigh its benefits, disclosure may be delayed until users have had the opportunity to apply the relevant patch.

The engineer must prepare formal, published security advisories with every fix release, stating CVE identifiers, CVSS scores, and installation instructions.

Typical solutions include publishing bulletins in the standardised, machine-readable CSAF (Common Security Advisory Framework) format, or posting advisories on GitHub Security Advisories and on a dedicated support web portal (a PSIRT portal).

**Point 5: coordinated vulnerability disclosure (CVD) policy**

The manufacturer must develop and maintain a Coordinated Vulnerability Disclosure (CVD) policy that lets external security researchers report discovered flaws.

The engineer, together with legal counsel, must create a publicly available CVD policy document detailing the rules for submitting information, safe-harbour assurances protecting good-faith researchers from liability, and the timeline for handling and remediating reported issues.

The technical solution is based on implementing disclosure processes in line with the international standard ISO/IEC 29147 and running an official report-intake programme, either directly or via bug-bounty platforms (HackerOne, Bugcrowd).

**Point 6: a vulnerability-reporting contact point and security.txt**

The manufacturer must provide a single point of contact for receiving vulnerability information and ensure it is stated in accompanying materials and on official web resources.

The engineer must create a secured email address for receiving reports and publish a standardised file with contact information and a PGP key for encrypting messages on the official website.

The practical solution is deploying a /.well-known/security.txt file per the RFC 9116 specification, listing links to the CVD policy, a PGP key, and an email address in the form security@company.com.

**Point 7: secure update-distribution mechanisms**

The manufacturer must ensure security updates are distributed through secure channels that guarantee the authenticity and integrity of the update files, ruling out tampering by attackers.

The engineer must build a digital-signing system for update images on isolated infrastructure, and configure the device's update agent to mandatorily verify the digital signature before unpacking or installing.

The typical solution uses The Update Framework (TUF) architecture for the update-repository infrastructure, applies component-signing tools (Cosign, GPG, RSA-4096/Ed25519), and delivers updates exclusively over encrypted HTTPS/TLS network channels.

**Point 8: security updates provided free of charge**

Security updates must be provided to users free of charge throughout the product's defined support period, unless otherwise agreed between the manufacturer and a business user for a tailor-made product — the same exception as in point 2(b).

The engineer must separate the release architecture so that new, paid product features are kept apart from critical security patches. Update-delivery servers must not require a valid paid subscription to download security patches.

The technical solution involves creating a separate public repository for security patches (security-updates.company.com), accessible to all released devices without subscription authentication.

**Technical compliance and implementation matrix**

For a summary view, the table below maps each point of Annex I to concrete tools, architectural patterns, and relevant standards.

| **Annex I point** | **Requirement of the regulation** | **Practical engineering solution/tool** | **Standard/specification used** |
| --- | --- | --- | --- |
| **Part I (1)** | Risk assessment and Security by Design | STRIDE/PASTA threat modelling, OWASP Threat Dragon | prEN 40000-1-2, ISO/IEC 21434 |
| **Part I (2a)** | Absence of known fixable CVEs | SCA scanning in CI/CD (Trivy, Snyk, Dependency-Check) | prEN 40000-1-4, CISA KEV, EUVD |
| **Part I (2b)** | Secure by Default & factory reset | Unique factory passwords, mandatory first-boot onboarding | ETSI EN 303 645, prEN 40000-1-4 |
| **Part I (2c)** | Auto-updates with opt-out | Dual-bank A/B OTA (RAUC, Mender), UI toggle | prEN 40000-1-4 |
| **Part I (2d)** | Access control and logging attempts | OAuth 2.0/mTLS, Fail2ban, PAM auditing | IEC 62443-4-2, prEN 40000-1-4 |
| **Part I (2e)** | Encryption at rest & in transit | TLS 1.3, AES-256-GCM, Secure Element/TPM 2.0 | FIPS 140-3, prEN 40000-1-4 |
| **Part I (2f)** | Protection of code and data integrity | Secure Boot (UEFI/ARM), dm-verity, HMAC checksums | prEN 40000-1-4 |
| **Part I (2g)** | Data-processing minimisation | Edge anonymisation, PII removal, local log TTL | GDPR Art. 25, prEN 40000-1-4 |
| **Part I (2h)** | DoS attack protection | HW watchdog, rate limiting, net.ipv4.tcp_syncookies | prEN 40000-1-4 |
| **Part I (2i)** | Isolation of system components | Docker/microVM (Firecracker), SELinux, microsegmentation | prEN 40000-1-4 |
| **Part I (2j)** | Attack-surface minimisation | JTAG blowing (eFuse), Yocto minimal images, distroless | prEN 40000-1-4 |
| **Part I (2k)** | Limiting attack propagation | Egress filtering, hardware DEP/NX bit, ASLR, W^X principle | prEN 40000-1-4 |
| **Part I (2l)** | Secure event logging | Syslog over TLS, auditd, cryptographic log chaining | prEN 40000-1-4 |
| **Part I (2m)** | Permanent data erasure | Crypto-shredding, NVMe Sanitize, eMMC Erase | prEN 40000-1-4 |
| **Part II (1)** | Building and maintaining the SBOM | Automated CycloneDX/SPDX generation (Syft, cdxgen) | prEN 40000-1-3, BSI TR-03183-2 |
| **Part II (2)** | Vulnerability remediation (patching) | Dependency-Track + Jira SLA workflows, hotfix git branches | prEN 40000-1-3, ISO/IEC 30111 |
| **Part II (3)** | Security testing | SAST (SonarQube), DAST (ZAP), fuzzing (AFL++), pentests | prEN 40000-1-3, BSI TR-03183-3 |
| **Part II (4)** | Public security bulletins | CSAF JSON advisories, GitHub Security Advisories | prEN 40000-1-3, ISO/IEC 29147 |
| **Part II (5)** | CVD policy | Public CVD policy (safe harbour), bug bounty (HackerOne) | prEN 40000-1-3, ISO/IEC 29147 |
| **Part II (6)** | Security contact & security.txt | /.well-known/security.txt (RFC 9116), PGP key | prEN 40000-1-3, RFC 9116 |
| **Part II (7)** | Update-channel protection | TUF (The Update Framework), Cosign/Ed25519 signing | prEN 40000-1-3 |
| **Part II (8)** | Free-of-charge patches | Public open CDN for patches, no authentication | prEN 40000-1-3 |

**Conclusions and practical recommendations**

The shift in the EU regulatory landscape requires companies to systematically rethink their approach to designing, developing, and supporting software and hardware products. The Annex I Part I requirements turn cybersecurity from an optional feature into a fundamental engineering characteristic of the product, without which market entry becomes legally impossible. At the same time, Annex I Part II requires building continuous DevSecOps processes focused on supply-chain transparency (via the SBOM) and rapid response to new threats.

Since the prEN 40000 series of harmonised standards is still in development, with submission to the Commission pushed to autumn/winter 2026, manufacturers are advised to build their own compliance systems based on existing international standards (ISO/IEC 29147, ISO/IEC 30111, IEC 62443, BSI TR-03183) in the meantime.

Particular attention should be paid to **11 September 2026**, when the mandatory Article 14 requirements take effect, to notify ENISA and national CSIRTs of actively exploited vulnerabilities and severe incidents within 24 hours. Full compliance with all the Annex I essential requirements, and completing the conformity assessment procedures for CE marking, become mandatory from **11 December 2027**.
