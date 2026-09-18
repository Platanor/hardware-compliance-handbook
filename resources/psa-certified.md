**PSA Certified — an independent IoT hardware security framework and certification scheme**

**What it is**

PSA Certified is a security framework and third-party certification scheme for connected devices, run by GlobalPlatform. It was founded by seven companies: Arm (semiconductor IP), Prove & Run (security consultancy, now trading as ProvenRun), four independent evaluation labs — SGS Brightsight, CAICT, Riscure, and UL — and TrustCB, who oversee and run the programme. Unlike the CRA and RED, it is not law — it is an independent baseline that a manufacturer can point to as external evidence of a security claim, evaluated at some levels by the manufacturer against a fixed questionnaire and at others directly by an independent lab (see certification levels below).

The scheme is built on two foundations that it expects every connected device to have:

- **10 Security Goals** — a short list of high-level security principles (e.g. unique device identity, secure boot, secure storage, secure communication, secure lifecycle) that apply regardless of product type.
- **PSA-RoT (PSA Root of Trust)** — a hardware-anchored root of trust built into the silicon: a set of implicitly-trusted functions (attestation, secure storage, cryptographic operations) that the rest of the device's software stack relies on. This is the same architectural concept referred to elsewhere in this repository as "secure boot" / "root of trust" in the context of Annex I Part I, point 2(f).

**Certification levels**

Levels 2 and above are evaluated directly by PSA-approved evaluation labs applying the SESIP methodology (Security Evaluation Standard for IoT Platforms) against a formal Protection Profile. Level 1 works differently: the manufacturer completes a fixed questionnaire (the PSA Certified Level 1 Questionnaire), which an approved evaluation lab then reviews and approves — not a lab-run technical evaluation, but not an unchecked self-declaration either.

| Level | What it covers |
| --- | --- |
| Level 1 | Questionnaire-based assessment against the 10 Security Goals, reviewed and approved by an approved evaluation lab. If the device is built on already-certified silicon and software, only the device-specific questions need answering — ~20 questions. |
| Level 2 | SESIP Profile evaluation providing evidence of protection against scalable, remote software attacks. As of the current scheme documents, this profile also absorbed what used to be a separate "RoT Component" certification track. |
| Level 3 | SESIP Profile evaluation providing evidence of protection against combined hardware and software attacks; a separate iSE/SE (integrated/external Secure Element) track exists at this tier too. |
| Level 4 | The most rigorous tier: iSE/SE SESIP Profile evaluation (includes the Level 4 RoT Component profile), for protection against hardware and software attacks at secure-element level. |
| API Certification | A separate track verifying conformance of the PSA cryptographic/attestation APIs, independent of device level. |

Four categories of vendor can hold a certification: silicon vendors, system software providers, IP providers, and device manufacturers — reflecting that a device's security posture is assembled from all four layers, not just the finished product. As of 14 September 2026, the scheme's public database lists 315 certifications from 122 companies (including STMicroelectronics, NXP, and Infineon on the silicon side), held by 80 different partners with PSA Certified certifications — check [products.psacertified.org](https://products.psacertified.org/) for the current count, since these numbers move.

**Why it's listed here**

PSA Certified is not required by the CRA, RED, or any other regulation covered in this repository, and holding a certification does not by itself satisfy any specific Annex I point or RED Article 3(3) requirement — there is no legal mapping between the scheme and EU law. It is listed as a **practical, independently-verified way to demonstrate** the underlying engineering claims that several requirements ask for:

- Annex I Part I, point 2(f) (integrity protection against unauthorised modification) — a PSA-RoT-based secure boot chain is a standard engineering answer to this requirement, and Level 2+ certification gives third-party evidence that the root of trust was implemented correctly, not just claimed.
- Annex I Part I, point 2(d) (protection from unauthorised access — authentication, identity, access management) and the RED cybersecurity delegated act's own authentication-related gaps in EN 18031 (see [`red/essential-requirements.md`](../red/essential-requirements.md) — the "no password escape hatch" restriction) — PSA-RoT's unique device identity and secure storage primitives are the hardware layer that a real authentication implementation sits on.

Treat it the same way as the ENISA playbook in this folder: a useful, independently-run cross-check for architecture decisions, not a substitute for the article-by-article legal analysis in `cra/` and `red/`.

**Source:** [psacertified.org](https://www.psacertified.org/) — scheme documents, certified-product database, and evaluation-lab directory are at [psacertified.org/development-resources](https://www.psacertified.org/development-resources/) and [products.psacertified.org](https://products.psacertified.org/). This is third-party, trademarked material (PSA Certified, GlobalPlatform) — not reproduced here beyond this summary; link out for the authoritative scheme text.
