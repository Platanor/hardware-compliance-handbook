**EN 40000: the first European standards for the Cyber Resilience Act — what device makers need to know**

*Status as of 20 November 2026. Standards move quickly; check the dates in the table against the sources at the end before relying on them.*

*A note on wording: under the CRA (Art. 3(36), via Regulation (EU) No 1025/2012) a standard becomes a **harmonised** standard only once its reference is published in the Official Journal of the EU. No EN 40000 part is there yet, so this page calls them "CRA standards", not "harmonised standards".*

**1. What EN 40000 is**

The Cyber Resilience Act (CRA, Regulation (EU) 2024/2847) sets legal security requirements for products with digital elements (Annex I), but it does not say *how* to meet them step by step. That is the job of European standards. In February 2025 the Commission asked CEN, CENELEC and ETSI for 41 standards (standardisation request **M/606**, Implementing Decision C(2025)618).

**EN 40000** is the CEN/CENELEC series that forms the horizontal backbone of that work — rules that apply to almost any connected product. Product-specific ("vertical") standards for higher-risk categories follow separately, mainly in the ETSI **EN 304 6xx** series and further CEN/CENELEC parts.

On **18 November 2026** the first CRA standard was published. The Commission describes it as generic principles and a common framework for managing cybersecurity from design and development through production, maintenance and end of support up to decommissioning — including cloud services that support a product function, such as remote control of a smart lock or storage of camera recordings.

**2. Status of the core parts**

| Standard | Topic | Status (20 Nov 2026) | Gives presumption of conformity today? |
|---|---|---|---|
| EN 40000-1-1 | Vocabulary | Published 18 Nov 2026 | No |
| EN 40000-1-2 | Principles, product risk management, lifecycle activities | Published 18 Nov 2026 | No |
| FprEN 40000-1-3 | Vulnerability handling (SBOM, disclosure, updates, advisories) | Final vote (reported); CEN gives no publication date, only "soon" | No — reported as the first candidate for citation |
| prEN 40000-1-4 | Generic security requirements (technical control catalogue) | Drafting; request deadline 30 Oct 2027 | No |

A standard gives **presumption of conformity** only once its reference is published in the Official Journal of the EU (CRA Art. 27(1)). As of this date, no CRA standard has been cited. Industry trackers report that CEN does not expect parts 1-1, 1-2 and 1-4 to be cited at all, with part 1-3 and the vertical standards as the main candidates. This is not yet confirmed by an official source.

**3. What each part asks you to do**

- **1-1 Vocabulary** — common terms. Use them consistently in your risk assessment, advisories and technical documentation.
- **1-2 Principles and lifecycle** — a risk-based process across the whole product life. Evidence is documentation: a product cybersecurity risk assessment (intended use, foreseeable misuse, supporting cloud services), your risk-treatment decisions, and plans for maintenance, end of support and decommissioning.
- **1-3 Vulnerability handling** — the operational side of Annex I Part II: a published disclosure policy and contact, an SBOM for every release, triage and fix workflow, free security updates, public advisories and post-release monitoring. Drafts reportedly let you reference upstream advisories for third-party components instead of duplicating them.
- **1-4 Generic security requirements** — a catalogue of technical controls for Annex I Part I(2)(a–m) (secure defaults, access control, confidentiality and integrity, updates, logging, attack-surface reduction). CEN-CENELEC has said it builds on the **EN 18031** series used under the Radio Equipment Directive.

**4. Dates that do not move**

| Date | What applies |
|---|---|
| 11 June 2026 | Rules for notified bodies (Chapter IV) |
| 11 September 2026 | Article 14 reporting of actively exploited vulnerabilities and severe incidents — already in force, **including for products placed on the market before 11 December 2027** (Art. 69(3)) |
| 11 December 2027 | All other CRA obligations: Annex I, technical documentation, conformity assessment, CE marking |

Delays in standards do not shift these dates. In November 2026 the Commission reportedly extended some M/606 deadlines by three months; this affects standards bodies, not manufacturers.

**5. Why it matters for your conformity route**

- **Default category:** you can self-assess with or without standards, but without a cited standard you must justify each Annex I requirement yourself.
- **Important Class I:** self-assessment is allowed only if you apply a cited harmonised standard (or common specification / certification scheme) **in full** (Art. 32(2)). If none is cited in time, you need a notified body.
- **Important Class II and Critical:** third-party assessment regardless.
- If standards are missing, the Commission can adopt **common specifications** instead (Art. 27(2)).
- Missing standards do **not** delay Article 14: it applies to all in-scope products, including those already on the market, since 11 September 2026.

**6. What to do now**

1. Classify every product (Default, Important Class I/II, Critical) and write down why.
2. Check whether a vertical standard covers your product (for example ETSI EN 304 627 for routers, EN 304 632 for smart locks and cameras — numbers as reported, confirm with ETSI).
3. Run and document a lifecycle risk assessment in the spirit of EN 40000-1-2, including your cloud backend and app.
4. Generate a machine-readable SBOM for every firmware release, automatically in CI.
5. Make sure you can meet Article 14: 24-hour early warning, 72-hour notification, and a final report — 14 days after a fix is available for an exploited vulnerability, or one month after the 72-hour notification for a severe incident. This already applies to devices you have sold.
6. Publish a vulnerability disclosure policy with a monitored security contact.
7. Ship signed firmware updates with rollback protection, unique per-device credentials, and closed debug ports. Use EN 18031 or ETSI EN 303 645 as the technical baseline until EN 40000-1-4 exists.
8. Decide and publish your support period — at least five years unless the product is expected to be used for less (Art. 13(8)). Five years is a **minimum, not a default**: if customers use the product longer, the support period should be longer (recital 60; Commission guidance). State the end date, at least month and year, **at the time of purchase** (Art. 13(19)).
9. For Class I products, line up a notified-body option in case no standard is cited in time.

**7. FAQ**

**Are EN 40000 standards mandatory?** No. Standards are voluntary; the CRA requirements are mandatory. A cited harmonised standard is simply the clearest way to show you meet them.

**Does applying EN 40000-1-2 today give presumption of conformity?** No. Only standards cited in the Official Journal do, and none is cited yet.

**We already follow IEC 62443, ETSI EN 303 645 or EN 18031. Is that enough?** It is a strong start — EN 18031 is the foundation of EN 40000-1-4 — but none of them gives CRA presumption of conformity, and they leave gaps around SBOMs, support periods and Article 14 reporting.

**Where can we get the standards?** From national standards bodies (for example PKN in Poland, DIN Media, BSI, NEN). Drafts can often be viewed free during public enquiry.

**What if standards arrive after December 2027?** The date stays. Default products document Annex I directly, Class I products go to a notified body, and the Commission may issue common specifications.

**Do we have to wait for standards before reporting under Article 14?** No. Reporting has applied since 11 September 2026, including for products placed on the market before December 2027 (Art. 69(3)).

**Sources**

Official:

- [European Commission — Guidance on the application of Regulation (EU) 2024/2847, OJ C/2026/6013 (17.11.2026)](http://data.europa.eu/eli/C/2026/6013/oj)
- [ENISA — Technical Advisory for Software Bill of Materials (22.10.2026)](https://www.enisa.europa.eu/publications/enisa-technical-advisory-for-software-bill-of-materials)
- [European Commission — First European standard published to support the Cyber Resilience Act (19.11.2026)](https://digital-strategy.ec.europa.eu/en/news/first-european-standard-published-support-cyber-resilience-act)
- [European Commission — Cyber Resilience Act: Standardisation](https://digital-strategy.ec.europa.eu/en/policies/cra-standardisation)
- [CEN-CENELEC — CRA Milestone Unlocked: First European standards supporting CRA (EN 40000-1-1, EN 40000-1-2), 19.11.2026](https://www.cencenelec.eu/news-events/news/2026/en-in-the-spotlight/2026-11-19-cra-standards-en-40000-1-1-and-en-40000-1-2/)
- [CEN-CENELEC — CRA Standards Unlocked: Deep Dive Session Security Controls (event page, 5.03.2026)](https://www.cencenelec.eu/news-events/events/2026/2026-03-05-cra-standards-unlocked-deep-dive-session-security-controls-generic-security-requirements/)
- [CEN-CENELEC — Deep Dive Session Security Controls – 40000-1-4 (slides PDF, 5.03.2026)](https://www.cencenelec.eu/media/CEN-CENELEC/Events/Webinars/2026/2026-03-05_cra_unlocked_deepdive_securitycontrols_cen-clc-jtc-13-wg-9_pt2.pdf)
- [CEN-CENELEC — Q&A report: Cybersecurity requirements for smart meter gateways (23.02.2026)](https://www.cencenelec.eu/media/CEN-CENELEC/Events/Webinars/2026/q-a_report_webinar_cra_unlocked_smart_meter_gateways_2026-02-23.pdf)
- [CEN-CENELEC — Question report (qa-report-0108)](https://www.cencenelec.eu/media/qa-report-0108.pdf)
- [CEN-CENELEC — Cyber Resilience Act: Standardization Request Officially Accepted (OTS 62, 2025)](https://www.cencenelec.eu/news-events/news/2025/newsletter/ots-62-cra/)
- [Orgalim — Cyber Resilience Act: Timely Citation of Harmonised Standards Essential (4.11.2026)](https://orgalim.eu/wp-content/uploads/Cyber-Resilience-Act-Timely-Citation-of-Harmonised-Standards-Essential-for-a-Secure-and-Competitive-European-Industry.pdf)

National standards bodies (where to find the documents):

- [DIN Media — DIN EN 40000-1-1:2026-03 (draft)](https://www.dinmedia.de/en/draft-standard/din-en-40000-1-1/399664868)
- [DIN Media — DIN EN 40000-1-2:2025-11 (draft)](https://www.dinmedia.de/en/draft-standard/din-en-40000-1-2/396310071)
- [SNV Connect — DIN EN 40000-1-2:2026](https://connect.snv.ch/en/din-en-40000-1-2-2026)
- [BSI — BS EN 40000-11 Essential cybersecurity requirements for products (project page)](https://standardsdevelopment.bsigroup.com/projects/2026-00676)
- [BDS (Bulgaria) — prБДС EN 40000-10:2026](https://bds-bg.org/en/project/show/bds:proj:129642)
- [Austrian Standards — Cyber Resilience Act seminar](https://www.austrian-standards.at/en/shop/academy/cyber-resilience-act~p4894864)
- [iTeh Standards — Draft ETSI EN 304 627 V1.0.1 (2026-07), sample PDF](https://cdn.standards.iteh.ai/samples/etsi/etsi-en-304-627-v1-0-1-2026-07-/a82c3678ed1246f8975b44c05f900c87/etsi-en-304-627-v1-0-1-2026-07-.pdf)

Legal texts and related guides:

- Standardisation request M/606, C(2025)618 — [`primary-sources/cra-standardisation-request-m606-c-2025-618.md`](../primary-sources/cra-standardisation-request-m606-c-2025-618.md)
- Regulation (EU) 2024/2847, Arts. 3(36), 13, 14, 27, 32, 69, 71 — [`primary-sources/cra-regulation-eu-2024-2847.md`](../primary-sources/cra-regulation-eu-2024-2847.md)
- Related: [`essential-requirements.md`](essential-requirements.md), [`product-risk-classes.md`](product-risk-classes.md), [`vulnerability-reporting.md`](vulnerability-reporting.md), [`timeline-deadlines.md`](timeline-deadlines.md)
