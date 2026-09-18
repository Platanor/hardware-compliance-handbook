**SBOM formats and specifications — CycloneDX, SPDX, and the 2026 minimum elements baseline**

**What it is**

A Software Bill of Materials (SBOM) is a structured, machine-readable inventory of a product's software components. Two independently governed specifications dominate real-world SBOM tooling today: **CycloneDX** and **SPDX**. A third, older standard — **SWID tags** — serves a related but different purpose and is being phased out of current SBOM guidance. Alongside the formats themselves, the **2026 CISA Minimum Elements for a Software Bill of Materials** (an international update that replaces the 2021 NTIA baseline) defines what data an SBOM actually needs to contain, independent of which format it's written in.

**CycloneDX**

| | |
| --- | --- |
| Current version | 1.7 (released 2025-10-21) |
| Developed by | OWASP Foundation and Ecma International (Technical Committee TC54) |
| Standardized as | ECMA-424 |
| Encodings | JSON, XML, Protocol Buffers |
| Media types | `application/vnd.cyclonedx+json`, `application/vnd.cyclonedx+xml`, `application/x.vnd.cyclonedx+protobuf` |
| File naming convention | `bom.json` / `bom.xml`, or `*.cdx.json` / `*.cdx.xml` |

CycloneDX's object model covers, among other things: **metadata** (supplier, manufacturer, tooling used to generate the BOM), **components** (the full first- and third-party inventory, including hardware, ML models, and cryptographic assets, not just software packages), **services**, **dependencies** (direct and transitive relationships), **vulnerabilities** (also usable for VEX — Vulnerability Exploitability eXchange — disclosures), and **formulation** (how a component was actually built or deployed). A 1.7.1 point release (schema-alignment and bug fixes across the XML/Protobuf schemas, no changes to `specVersion`) followed on 2 June 2026. CycloneDX 2.0 is expected in autumn 2026, with Ecma ratification planned for December 2026.

**SPDX**

| | |
| --- | --- |
| Current ISO standard | ISO/IEC 5962:2021 (standardizes SPDX 2.2.1) |
| Latest specification release | SPDX 3.0.0 (April 2024) |
| ISO status of 3.0 | Draft International Standard (ISO/IEC DIS 5962 v3.0) in the ISO member enquiry phase — not yet a published ISO standard as of 15 September 2026 |
| Governed by | The Linux Foundation (SPDX project) |
| Encodings | JSON, YAML, RDF/XML, tag-value, spreadsheet |

SPDX 3.0 restructured the format around eight **profiles** — core, software, security, build, AI, dataset, licensing, and lite — so a document only needs to carry the fields relevant to its use case rather than one fixed schema for everything. The lite profile originates from the OpenChain Japan Work Group and was introduced in SPDX 2.2 (2020) as a lightweight subset for license-compliance workflows in the Japanese supply chain — it predates the 2021 NTIA minimum elements. SPDX 2.3 (November 2022) then updated the lite profile's Annex G to include the NTIA mandatory minimum fields. SPDX 2.3 also remains what most current SBOM-generation tooling actually emits by default — see the worked SPDX example in [`examples.md`](examples.md), which uses SPDX 2.3 JSON for exactly this reason.

**SWID tags — a related but different standard**

SWID (Software Identification) tags, defined by **ISO/IEC 19770-2:2015**, are XML records that identify a specific installed instance of a software product on a device — added at install time, removed at uninstall. This is a different job than CycloneDX or SPDX, which describe the components that went into building a release artifact. Earlier NTIA-era SBOM guidance listed SWID as one of three viable SBOM formats; the 2026 CISA minimum elements guidance (below) no longer includes it, leaving CycloneDX and SPDX as the two recognized machine-processable SBOM formats in current US/international guidance.

**CycloneDX vs SPDX — what each was designed for**

The two formats grew out of different problems, and that heritage still shows. CycloneDX grew out of application-security tooling and is built security-first: its object model treats vulnerabilities, VEX, and formulation (how a component was actually built) as first-class citizens, with license data as a secondary concern. SPDX grew out of license-compliance tooling, and that heritage is why it carries an ISO number (ISO/IEC 5962) rather than just a project name — a property some procurement and legal processes specifically look for.

Neither format is mandated by the CRA, and the choice between them is not yet a settled question. CRA Article 13(24) gives the Commission the power to specify the SBOM's format and elements by implementing act, "taking into account European or international standards and best practices" — but as of 15 September 2026, no such implementing act has been adopted. Until one is, picking CycloneDX or SPDX today is a working decision made against current tooling and audience, not a final compliance choice; the Commission could later name one of the two, both, or neither.

**The 2026 minimum elements: what an SBOM must actually contain**

Format is only half the picture — a CycloneDX or SPDX file can still be a low-value SBOM if it's missing the right data. On 29 July 2026, CISA published the **2026 Minimum Elements for a Software Bill of Materials**, co-authored with the NSA, the FBI, and international partner cybersecurity agencies. It replaces the original 2021 NTIA minimum elements — the document that, for five years, was the de facto baseline referenced by US federal procurement rules and by other regulators' SBOM guidance (including, for medical devices, the FDA).

The table below shows only what changed — the new fields required on top of the 2021 baseline, and the fields that were renamed:

| Change | Field |
| --- | --- |
| New (SBOM Metadata) | SBOM Author Signature — a digital signature over the SBOM document itself |
| New (SBOM Metadata) | SBOM Data Format Name (e.g., "CycloneDX") |
| New (SBOM Metadata) | SBOM Data Format Version (e.g., "1.7") |
| New (SBOM Metadata) | SBOM Generation Context — produced before build from source, during the build, or reverse-engineered after build from the binary |
| New (SBOM Metadata) | SBOM Tool Name |
| New (SBOM Metadata) | SBOM Tool Version |
| New (SBOM Metadata) | SBOM Version — a version identifier for the SBOM document itself |
| New (Component Data) | Component Hash Value — previously only "recommended," now mandatory |
| New (Component Data) | Component Hash Algorithm |
| New (Component Data) | Component License |
| Renamed | "Author of SBOM Data" → **SBOM Author** |
| Renamed | "Supplier" → **Component Producer** |
| Renamed | "Version of the Component" → **Component Version** |
| Renamed | "Other Unique Identifiers" → **Component Identifiers** (at least one machine-processable identifier, such as a PURL or CPE, is now required per component) |

Coverage expectations also tightened, separately from the field list above: the 2026 guidance requires **all** direct and transitive dependencies, explicitly stating there is "no minimum depth," compared to 2021's more limited "top-level dependencies" requirement.

Full text: [2026 CISA Minimum Elements for SBOM (PDF)](https://www.cisa.gov/sites/default/files/2026-07/2026_cisa_sbom_minimum_elements_508c.pdf).

**How adoption is actually going**

ENISA's *[SBOM Adoption State of Play — 2026](https://www.enisa.europa.eu/publications/sbom-adoption-state-of-play-2026)* (published 9 June 2026 — a survey of 334 organisations, 65% EU-based, 80% directly affected by the CRA) found that 78% had already started implementing SBOMs, though the same survey puts only 9% at a mature level and 44% still in a pilot or limited-deployment stage; 79% expected to reach CRA-relevant SBOM maturity by the time the regulation fully applies (December 2027), with the CRA cited as the main driver of adoption. It's a survey of where the field currently stands, not implementation guidance, so it's cited here as context rather than as a how-to source.

**See it in practice**

This page explains what CycloneDX and SPDX are; it doesn't show what a file in either format actually looks like. For that, see [`examples.md`](examples.md) — a hand-built, schema-checked example of the same hypothetical device's SBOM written out in both formats side by side, plus a CycloneDX example with an embedded VEX statement. For real, complete, production-grade examples (not illustrative ones), use the format projects' own official example repositories: [CycloneDX/bom-examples](https://github.com/CycloneDX/bom-examples) and the [SPDX examples page](https://spdx.dev/use/examples/).

**Why it's listed here**

CRA Annex I, Part II, point 1 requires manufacturers to identify and document vulnerabilities and components, "including by drawing up a software bill of materials in a commonly used and machine-readable format covering at the very least the top-level dependencies of the products" (see [`../cra/essential-requirements.md`](../cra/essential-requirements.md)) — but the regulation itself does not name a specific SBOM format. Note the exact wording: "top-level dependencies," not "direct dependencies" in the npm/pip sense of immediate imports — this is why the CISA "no minimum depth" requirement described above is a real, substantive step beyond the CRA floor, not just a stricter phrasing of the same thing. CycloneDX and SPDX are the two formats a manufacturer's tooling will, in practice, actually produce ([Syft](https://github.com/anchore/syft), the CycloneDX CLI, and cdxgen all export to one or both), which is why that file already references them directly. This page explains what those two formats actually are, how they're governed and versioned, and what the current (2026) international baseline expects an SBOM to contain — independent of which of the two formats is used to express it. For the closely related question of documenting whether a given vulnerability in the SBOM actually matters for this product, see [`vex.md`](vex.md).

**Source:** [cyclonedx.org/specification/overview](https://cyclonedx.org/specification/overview), [spdx.dev/about/overview](https://spdx.dev/about/overview/), [ISO/IEC 19770-2:2015](https://www.iso.org/standard/65666.html), [2026 CISA Minimum Elements for SBOM](https://www.cisa.gov/resources-tools/resources/2026-minimum-elements-software-bill-materials-sbom). CycloneDX and SPDX are independently governed, trademarked specifications (OWASP/Ecma International and the Linux Foundation respectively) — summarized here, not reproduced; use the official documentation and example repositories linked above as the source of truth.
