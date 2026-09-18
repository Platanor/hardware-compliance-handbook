**VEX — Vulnerability Exploitability eXchange: three specifications, one purpose**

**What it is**

VEX (Vulnerability Exploitability eXchange) is not a single specification but a shared concept, implemented by three separate, independently governed formats: **CycloneDX VEX**, **CSAF VEX**, and **OpenVEX**. All three let a software supplier make a machine-readable statement about whether a specific vulnerability (CVE) actually affects a specific product. VEX is a companion to an SBOM, not a replacement for one: the SBOM says "these components are in the product"; VEX says "and here is what we currently know about which of the vulnerabilities in those components actually matter here."

**The three implementations**

| | CycloneDX VEX | CSAF VEX | OpenVEX |
| --- | --- | --- | --- |
| Governed by | OWASP Foundation + Ecma International (same governance as CycloneDX itself) | OASIS Open (CSAF Technical Committee) — CSAF 2.0 itself was also published as **ISO/IEC 20153:2025** on 21 February 2025, so this line carries an ISO number too, not only the SPDX line on the neighbouring page | Open Source Security Foundation (OpenSSF) — the spec itself is explicitly marked as a **draft** in its own repository, unlike the other two |
| Format | An extension of the CycloneDX BOM format itself — a `vulnerabilities` array with an `analysis` block — so a VEX statement and an SBOM can travel as one file | A profile within CSAF 2.0 (published November 2022, the successor to the older CVRF format) — `document` / `product_tree` / `vulnerabilities` sections | A minimal, SBOM-format-agnostic JSON-LD document |
| Typical fit | When the SBOM and the VEX statement should travel together as a single CycloneDX file | Formal security-advisory publishing (vendor PSIRT bulletins) | Lightweight, tool-friendly VEX for CI/CD pipelines; built-in support for signing with Sigstore |

**A vocabulary mismatch worth knowing about**

CISA's *Minimum Requirements for VEX* (v1.0.0, April 2023, developed by an international working group building on the original 2021 NTIA-era VEX initiative) defines four statuses a VEX statement can assert: `not_affected`, `affected`, `fixed`, `under_investigation`. OpenVEX and CSAF VEX both use this vocabulary directly. CycloneDX's own `analysis.state` field uses a different vocabulary instead: `exploitable`, `in_triage`, `resolved`, `resolved_with_pedigree`, `false_positive`, `not_affected` — only `not_affected` is shared between the two systems. A tool built to consume one VEX flavor will not recognize the other's status values beyond that single overlap; this matters when picking tooling that has to read VEX statements from suppliers who may use either vocabulary.

**See it in practice**

[`examples.md`](examples.md) includes a worked CycloneDX example with a `vulnerabilities` entry carrying a full `analysis` block (`state`, `justification`, `detail`) — the CycloneDX VEX flavor from the table above, shown embedded directly in an SBOM rather than described in the abstract.

**Why it's listed here**

VEX is not a CRA-named format and does not appear in Annex I by name. But it directly serves one specific, defensible obligation: Annex I Part II point (2) requires manufacturers to "address and remediate vulnerabilities without delay" (see [`../cra/essential-requirements.md`](../cra/essential-requirements.md)).

One correction worth stating plainly, because getting it wrong here is costly: **VEX is not a mechanism for skipping a report or an exemption from remediation.** The Article 14 trigger for mandatory 24-hour notification is an *actively exploited* vulnerability — defined in Article 3, point (42), as one with "reliable evidence that a malicious actor has exploited it ... without permission of the system owner." A VEX statement asserting `not_affected`, or documenting why a fix is being deferred, does not change that trigger and provides no exemption from it — an actively exploited vulnerability is reportable whether or not a VEX statement exists. What VEX actually provides is an evidentiary record: a dated, structured statement of *why* a manufacturer judged a given CVE not urgent enough to patch immediately, which is exactly the kind of documentation a manufacturer would want on hand to justify an "address and remediate ... without delay" position to a market surveillance authority reviewing that decision later. That is a narrower and more accurate claim than "VEX means you don't have to report."

**Source:** [cyclonedx.org/capabilities/vex](https://cyclonedx.org/capabilities/vex/), [OASIS CSAF 2.0 specification](https://docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html), [ISO/IEC 20153:2025](https://www.iso.org/standard/89986.html) (published 21 February 2025, stage 60.60), [OpenVEX specification](https://github.com/openvex/spec/blob/main/OPENVEX-SPEC.md), [CISA Minimum Requirements for VEX (PDF, April 2023)](https://www.cisa.gov/sites/default/files/2023-04/minimum-requirements-for-vex-508c.pdf). All three VEX implementations are independently governed specifications — summarized here, not reproduced; use the official documentation linked above as the source of truth.
