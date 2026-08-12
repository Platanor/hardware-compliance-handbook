**Directive (EU) 2022/2555 (NIS2) overview: scope, structure, and why it's different from the CRA and RED**

**Background, regulatory context, and objective**

Directive (EU) 2022/2555, known as **NIS2**, was adopted on 14 December 2022, published in the OJ on 27 December 2022, and entered into force on **16 January 2023** (twentieth day after publication). It repeals and replaces the original NIS Directive (Directive (EU) 2016/1148, "NIS1"), with the repeal taking effect on **18 October 2024** — the same date NIS2's own transposed obligations became applicable.

**The single most important thing to understand about NIS2 before comparing it to the CRA or RED: NIS2 regulates entities, not products.** The CRA sets requirements for what a connected *product* must do before it can be sold in the EU. RED does the same for *radio equipment* specifically. NIS2 sets requirements for how certain *organisations* — because of the sector they operate in and their size — must manage cybersecurity risk across their own operations and report incidents. A hardware manufacturer can be in scope of the CRA (because it makes products with digital elements) and simultaneously be in or out of scope of NIS2 (depending on whether it, as an *organisation*, falls in an Annex I or II sector and meets the size threshold) — these are two separate questions.

**Key dates**

| Date | Event |
| --- | --- |
| 14 December 2022 | Directive adopted |
| 27 December 2022 | Published in the OJ (L 333/80) |
| **16 January 2023** | Entry into force |
| 17 January 2025 | Deadline for the Cooperation Group to establish peer-review methodology (Art. 19); deadline for Member States to notify the Commission of national penalty rules (Art. 36) |
| 17 April 2025 | Deadline for Member States to establish their national list of essential/important entities (Art. 3(3)) |
| **17 October 2024** | Deadline for Member States to adopt and publish national transposing measures (Art. 41(1)) |
| **18 October 2024** | NIS2's transposed obligations become applicable; Directive (EU) 2016/1148 (NIS1) repealed (Art. 44) |
| 17 October 2027 | First Commission review of the Directive's functioning (Art. 40), then every 36 months |

**Who is in scope (Article 2)**

NIS2 applies to public or private entities that:

1. Fall within a sector or subsector listed in **Annex I** (11 "sectors of high criticality") or **Annex II** (7 "other critical sectors"), **and**
2. Qualify as at least a **medium-sized enterprise** under the EU's size-threshold Recommendation (2003/361/EC) — broadly, 50+ employees or €10M+ annual turnover/balance sheet.

**Regardless of size**, NIS2 also applies to specific categories named in Article 2(2): providers of public electronic communications networks/services, trust service providers, TLD registries and DNS service providers; entities that are the sole provider of an essential service in a Member State; entities whose disruption could significantly affect public safety/security/health or cause cross-border systemic risk; entities critical at national/regional level; and certain public administration entities. Entities already identified as "critical entities" under the separate Critical Entities Resilience Directive (EU) 2022/2557 are automatically in scope regardless of size, as are entities providing domain name registration services.

**Micro and small enterprises are generally out of scope**, unless they fall into one of the size-independent categories above.

**Essential vs. important entities (Article 3)**

NIS2 splits in-scope entities into two categories, and the category determines which supervisory regime applies — this is a structurally different sorting than the CRA's four-tier risk classification (Default/Important I/Important II/Critical).

- **Essential entities**: Annex I entities that exceed the medium-enterprise ceiling (i.e., large enterprises in high-criticality sectors); qualified trust service providers, TLD registries and DNS providers regardless of size; certain public electronic communications providers; central-government public administration entities; entities a Member State chooses to designate as essential under Art. 2(2)(b)-(e); entities identified as critical entities under Directive (EU) 2022/2557; and, at a Member State's option, entities it had already classified as operators of essential services under the old NIS1 regime.
- **Important entities**: everything else in scope — i.e., Annex I or II entities that don't meet the "essential" criteria above.

The practical consequence (detailed in `obligations.md`): essential entities face **proactive** supervision (regular inspections and audits, whether or not anything has gone wrong); important entities face **reactive, ex post** supervision only (checked when there's already evidence of a problem).

**Member States must establish and maintain a public list of essential and important entities by 17 April 2025**, reviewed at least every two years.

**Structural anatomy of the directive**

NIS2 has 9 chapters (46 articles) and 3 annexes:

- **Chapter I** (Art. 1-6) — subject matter, scope, essential/important entity classification, sector-specific-law interaction, minimum harmonisation, definitions.
- **Chapter II** (Art. 7-13) — coordinated cybersecurity frameworks: national strategy, competent authorities, single points of contact, cyber crisis management, CSIRTs, coordinated vulnerability disclosure.
- **Chapter III** (Art. 14-19) — cooperation at Union/international level: Cooperation Group, CSIRTs network, EU-CyCLONe, state-of-cybersecurity reporting, peer reviews.
- **Chapter IV** (Art. 20-25) — **cybersecurity risk-management measures and reporting obligations**: this is the substantive chapter (governance, the Art. 21 measures list, supply-chain risk assessment, the Art. 23 incident-reporting clock, certification schemes, standardisation).
- **Chapter V** (Art. 26-28) — jurisdiction and registration.
- **Chapter VI** — [cross-references to the Art. 24 certification delegated-act power].
- **Chapter VII** (Art. 31-37) — supervision and enforcement: the essential-vs-important supervisory split (Art. 32/33), administrative fines (Art. 34).
- **Chapter VIII** (Art. 38-39) — delegated and implementing acts.
- **Chapter IX** (Art. 40-46) — final provisions: review, transposition, repeal of NIS1, entry into force.
- **Annex I** — 11 sectors of high criticality (Energy, Transport, Banking, Financial market infrastructures, Health, Drinking water, Waste water, Digital infrastructure, ICT service management B2B, Public administration, Space).
- **Annex II** — 7 other critical sectors (Postal/courier, Waste management, Chemicals, Food, Manufacturing, Digital providers, Research).
- **Annex III** — correlation table mapping NIS1 provisions to NIS2 equivalents (procedural, not reproduced in this repository's primary-source copy).

**How NIS2 relates to the CRA and RED**

See [`../relationship-to-other-eu-law.md`](../relationship-to-other-eu-law.md) for the full picture. In short: a hardware/IoT manufacturer whose own organisation falls into an Annex I sector (e.g., it also operates critical digital infrastructure, or is large enough and sector-classified as an ICT managed-security-service provider) may face NIS2 obligations about *how it runs its own operations*, entirely separate from whatever CRA/RED obligations apply to the *products* it sells. Most product-focused hardware manufacturers building consumer or industrial IoT devices will not themselves be NIS2 in-scope entities unless they also provide one of the Annex I/II services — but their *customers*, if those customers are NIS2 essential/important entities, may pass down supply-chain security expectations under NIS2 Article 21(2)(d), which explicitly names "supply chain security" as a required risk-management measure.
