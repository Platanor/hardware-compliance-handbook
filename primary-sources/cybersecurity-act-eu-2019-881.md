> **Source:** EUR-Lex, CELEX [32019R0881](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:32019R0881) — Regulation (EU) 2019/881 of the European Parliament and of the Council of 17 April 2019 on ENISA (the European Union Agency for Cybersecurity) and on information and communications technology cybersecurity certification and repealing Regulation (EU) No 526/2013 (Cybersecurity Act).
>
> **Retrieved:** 2026-08-11, via JavaScript-rendered extraction (Claude in Chrome) of the EUR-Lex HTML consolidated view, `id="enc_1"` (enacting terms) and `id="anx_1"` (Annex).
>
> **Conversion method:** the enacting terms were pulled in three sequential windows from `document.getElementById('enc_1').innerText` and the Annex from `document.getElementById('anx_1').innerText`; reformatted to Markdown headings by article/title/chapter. No wording was altered — this is a direct text extraction, not a paraphrase.
>
> **Coverage:** enacting terms (Articles 1–69, complete) and the Annex ("Requirements to be met by conformity assessment bodies", complete). **Recitals (preamble) were not captured** — only the operative articles and the Annex. If you need a recital, go to the authoritative EUR-Lex page linked above.
>
> **Authoritative version:** always defer to the official EUR-Lex text (and the Official Journal PDF) over this copy in case of any discrepancy. This is a working mirror for LLM/RAG convenience, not a legal source of record.

## Key locations

| Provision | What it says | Why we cite it |
| --- | --- | --- |
| Art. 2(9)–(11) | Defines "European cybersecurity certification scheme", "national cybersecurity certification scheme", "European cybersecurity certificate" | Core vocabulary for Title III (certification framework) |
| Art. 46 | Establishes the European cybersecurity certification framework | The legal basis for EUCC and any future scheme |
| Art. 52 | Assurance levels: basic / substantial / high | Central to understanding what a certificate actually attests |
| Art. 53 | Conformity self-assessment (EU statement of conformity) — permitted only for assurance level "basic" | Distinguishes self-assessment from third-party certification, relevant to how this compares to CRA's own self-assessment/notified-body split |
| Art. 56(2)–(3) | Cybersecurity certification is voluntary unless made mandatory by other Union/Member State law; Commission must periodically assess whether to make schemes mandatory | Explains why EUCC certification is not (yet) a mandatory CE-marking-style requirement, unlike CRA |
| Art. 56(4)–(6) | Who can issue certificates at "basic"/"substantial" vs. "high" assurance levels | Practical routing: conformity assessment body vs. national authority |
| Art. 58 | National cybersecurity certification authorities — designation, independence, powers | Who supervises/enforces certification nationally |
| Art. 65 | Penalties — left to Member State law (like RED, unlike CRA) | Cross-regime penalty comparison |
| Annex, points 1–20 | Requirements for conformity assessment bodies (independence, competence, confidentiality, liability insurance, etc.) | Relevant if a manufacturer is evaluating which body to use for EUCC certification |

## Related files

- [`../csa/overview.md`](../csa/overview.md) — processed guide: what the CSA is and how it differs from CRA/RED/NIS2
- [`../csa/eucc-certification.md`](../csa/eucc-certification.md) — processed guide: the EUCC scheme specifically, assurance levels, voluntary-vs-mandatory status
- [`../relationship-to-other-eu-law.md`](../relationship-to-other-eu-law.md) — cross-cutting comparison with CRA, RED, NIS2, GDPR, AI Act

---

# TITLE I — GENERAL PROVISIONS

### Article 1 — Subject matter and scope

1. With a view to ensuring the proper functioning of the internal market while aiming to achieve a high level of cybersecurity, cyber resilience and trust within the Union, this Regulation lays down:

(a) objectives, tasks and organisational matters relating to ENISA (the European Union Agency for Cybersecurity); and

(b) a framework for the establishment of European cybersecurity certification schemes for the purpose of ensuring an adequate level of cybersecurity for ICT products, ICT services and ICT processes in the Union, as well as for the purpose of avoiding the fragmentation of the internal market with regard to cybersecurity certification schemes in the Union.

The framework referred to in point (b) of the first subparagraph applies without prejudice to specific provisions in other Union legal acts regarding voluntary or mandatory certification.

2. This Regulation is without prejudice to the competences of the Member States regarding activities concerning public security, defence, national security and the activities of the State in areas of criminal law.

### Article 2 — Definitions

For the purposes of this Regulation, the following definitions apply:

(1) 'cybersecurity' means the activities necessary to protect network and information systems, the users of such systems, and other persons affected by cyber threats;

(2)–(8) definitions incorporated by reference from Directive (EU) 2016/1148 (network and information system; national NIS strategy; operator of essential services; digital service provider; incident; incident handling), plus (8) 'cyber threat' means any potential circumstance, event or action that could damage, disrupt or otherwise adversely impact network and information systems, the users of such systems and other persons;

(9) 'European cybersecurity certification scheme' means a comprehensive set of rules, technical requirements, standards and procedures that are established at Union level and that apply to the certification or conformity assessment of specific ICT products, ICT services or ICT processes;

(10) 'national cybersecurity certification scheme' means a comprehensive set of rules, technical requirements, standards and procedures developed and adopted by a national public authority and that apply to the certification or conformity assessment of ICT products, ICT services and ICT processes falling under the scope of the specific scheme;

(11) 'European cybersecurity certificate' means a document issued by a relevant body, attesting that a given ICT product, ICT service or ICT process has been evaluated for compliance with specific security requirements laid down in a European cybersecurity certification scheme;

(12) 'ICT product' means an element or a group of elements of a network or information system;

(13) 'ICT service' means a service consisting fully or mainly in the transmission, storing, retrieving or processing of information by means of network and information systems;

(14) 'ICT process' means a set of activities performed to design, develop, deliver or maintain an ICT product or ICT service;

(15)–(20) definitions incorporated by reference from Regulation (EC) No 765/2008 and Regulation (EU) No 1025/2012: accreditation, national accreditation body, conformity assessment, conformity assessment body, standard, and 'technical specification' means a document that prescribes the technical requirements to be met by, or conformity assessment procedures relating to, an ICT product, ICT service or ICT process;

(21) 'assurance level' means a basis for confidence that an ICT product, ICT service or ICT process meets the security requirements of a specific European cybersecurity certification scheme, indicates the level at which an ICT product, ICT service or ICT process has been evaluated but as such does not measure the security of the ICT product, ICT service or ICT process concerned;

(22) 'conformity self-assessment' means an action carried out by a manufacturer or provider of ICT products, ICT services or ICT processes, which evaluates whether those ICT products, ICT services or ICT processes meet the requirements of a specific European cybersecurity certification scheme.

# TITLE II — ENISA (THE EUROPEAN UNION AGENCY FOR CYBERSECURITY)

## CHAPTER I — Mandate and objectives

### Article 3 — Mandate

ENISA carries out its tasks to achieve a high common level of cybersecurity across the Union, acting as a reference point for advice and expertise for Union institutions and stakeholders, contributing to reducing fragmentation of the internal market, and acting independently while avoiding duplication of Member State activities.

### Article 4 — Objectives

ENISA is to be a centre of expertise on cybersecurity; assist Union institutions and Member States in developing and implementing cybersecurity policy; support capacity-building and preparedness; promote cooperation and information sharing; contribute to increasing Union-level cybersecurity capabilities; **promote the use of European cybersecurity certification and contribute to establishing and maintaining the European cybersecurity certification framework under Title III** (Art. 4(6)); and promote cybersecurity awareness including cyber-hygiene and cyber-literacy.

## CHAPTER II — Tasks (Articles 5–12)

Summarized — full detail in the primary text if needed:

- **Art. 5** — Development and implementation of Union policy and law: ENISA assists and advises on cybersecurity policy/law, supports consistent Member State implementation of Directive (EU) 2016/1148 (the original NIS Directive), contributes to the Cooperation Group, and prepares annual state-of-implementation reports.
- **Art. 6** — Capacity-building: assists Member States and Union institutions/bodies in improving prevention, detection, analysis and response to cyber threats; supports national CSIRT development; organises biennial Union-level cybersecurity exercises; supports information sharing across sectors.
- **Art. 7** — Operational cooperation at Union level: ENISA provides the secretariat of the CSIRTs network, supports Member States within it, organises regular cybersecurity exercises (large-scale exercise at least biennially), and prepares a regular EU Cybersecurity Technical Situation Report.
- **Art. 8** — **Market, cybersecurity certification, and standardisation**: ENISA monitors standardisation developments and recommends technical specifications where standards are unavailable; **prepares candidate European cybersecurity certification schemes** (Art. 8(1)(b), cross-referencing Art. 49); evaluates adopted schemes; provides the secretariat of the Stakeholder Cybersecurity Certification Group; compiles guidelines and good practices on cybersecurity requirements; performs and disseminates analyses of the cybersecurity market.
- **Art. 9** — Knowledge and information: analyses emerging technologies, performs long-term strategic threat analyses, provides advice on infrastructure security, pools cybersecurity information via a dedicated portal.
- **Art. 10** — Awareness-raising and education.
- **Art. 11** — Research and innovation: advises on research priorities, may participate in research/innovation funding programmes.
- **Art. 12** — International cooperation with third countries and international organisations.

## CHAPTER III — Organisation of ENISA (Articles 13–23)

Governance structure: Management Board (Art. 14–18, one member per Member State plus two Commission members, four-year renewable terms, adopts the single programming document and budget), Executive Board (Art. 19, five members, prepares Management Board decisions), Executive Director (Art. 20, day-to-day administration, five-year term renewable once), ENISA Advisory Group (Art. 21, stakeholder advisory body, excludes Title III certification matters), Stakeholder Cybersecurity Certification Group (Art. 22, advises specifically on the certification framework and the Union rolling work programme), National Liaison Officers Network (Art. 23).

## CHAPTER IV — Establishment and structure of ENISA's budget (Articles 24–33)

Single programming document (Art. 24, adopted annually by 30 November), declarations of interest (Art. 25), transparency (Art. 26), confidentiality (Art. 27), access to documents under Regulation (EC) No 1049/2001 (Art. 28), budget establishment (Art. 29), budget structure — contribution from the Union budget, assigned revenue, delegation agreements, third-country contributions, voluntary Member State contributions (Art. 30), budget implementation and discharge procedure (Art. 31), financial rules (Art. 32), anti-fraud measures via OLAF (Art. 33).

## CHAPTER V — Staff (Articles 34–37)

Staff Regulations of Officials apply (Art. 34); privileges and immunities (Art. 35); Executive Director appointment/removal procedure, statement before European Parliament committee, five-year term extendable once by five years (Art. 36); seconded national experts (Art. 37).

## CHAPTER VI — General provisions concerning ENISA (Articles 38–45)

Legal status — ENISA is a Union body with legal personality (Art. 38); liability, contractual and non-contractual, Court of Justice jurisdiction (Art. 39); language arrangements (Art. 40); protection of personal data under Regulation (EU) 2018/1725 (Art. 41); cooperation with third countries and international organisations (Art. 42); security rules for classified/sensitive information (Art. 43); headquarters agreement with host Member State (Art. 44); administrative control by the European Ombudsman (Art. 45).

# TITLE III — CYBERSECURITY CERTIFICATION FRAMEWORK

### Article 46 — European cybersecurity certification framework

1. The European cybersecurity certification framework shall be established in order to improve the conditions for the functioning of the internal market by increasing the level of cybersecurity within the Union and enabling a harmonised approach at Union level to European cybersecurity certification schemes, with a view to creating a digital single market for ICT products, ICT services and ICT processes.

2. The European cybersecurity certification framework shall provide for a mechanism to establish European cybersecurity certification schemes and to attest that the ICT products, ICT services and ICT processes that have been evaluated in accordance with such schemes comply with specified security requirements for the purpose of protecting the availability, authenticity, integrity or confidentiality of stored or transmitted or processed data or the functions or services offered by, or accessible via, those products, services and processes throughout their life cycle.

### Article 47 — The Union rolling work programme for European cybersecurity certification

The Commission publishes a Union rolling work programme identifying strategic priorities for future schemes, based on the availability/development of national schemes (risk of fragmentation), relevant Union/Member State law or policy, market demand, cyber threat landscape developments, or ECCG request. The first rolling work programme was due by 28 June 2020, updated at least every three years.

### Article 48 — Request for a European cybersecurity certification scheme

The Commission may request ENISA to prepare a candidate scheme based on the rolling work programme; in duly justified cases the Commission or the ECCG may request a candidate scheme not on the programme.

### Article 49 — Preparation, adoption and review of a European cybersecurity certification scheme

ENISA prepares candidate schemes following formal, open, transparent stakeholder consultation, with an ad hoc working group and close cooperation with the ECCG (which adopts an opinion, non-binding on ENISA). The Commission then **may adopt implementing acts** providing for a scheme meeting Articles 51, 52 and 54 (Art. 49(7)) — this is how a candidate scheme becomes a legally adopted European cybersecurity certification scheme, such as the EUCC. Each adopted scheme is evaluated by ENISA at least every five years (Art. 49(8)).

### Article 50 — Website on European cybersecurity certification schemes

ENISA maintains a dedicated public website listing schemes, certificates, EU statements of conformity, including expired/withdrawn ones.

### Article 51 — Security objectives of European cybersecurity certification schemes

A scheme must be designed to achieve, as applicable: protection against accidental/unauthorised storage, processing, access or disclosure of data; protection against accidental/unauthorised destruction, loss, alteration or unavailability; access restricted to authorised persons/programs/machines; identification and documentation of known dependencies and vulnerabilities; recording of access/use; ability to check who accessed what and when; verification of absence of known vulnerabilities; timely restoration of availability after an incident; **secure by default and by design**; up-to-date software/hardware free of publicly known vulnerabilities, with secure-update mechanisms.

### Article 52 — Assurance levels of European cybersecurity certification schemes

1. A scheme may specify one or more assurance levels: **'basic', 'substantial' or 'high'**, commensurate with the risk associated with the intended use (probability and impact of an incident).

5. **'Basic'** — assurance that products meet security requirements and have been evaluated at a level intended to minimise known basic risks; evaluation activities include at least a review of technical documentation (or an equivalent substitute).

6. **'Substantial'** — assurance intended to minimise known cybersecurity risks and risk of incidents/cyberattacks by actors with limited skills and resources; evaluation includes at least a review demonstrating absence of publicly known vulnerabilities, plus testing that security functionalities are correctly implemented.

7. **'High'** — assurance intended to minimise the risk of state-of-the-art cyberattacks by actors with significant skills and resources; evaluation includes at least a review for absence of publicly known vulnerabilities, testing of correct implementation of security functionalities at the state of the art, **and an assessment of resistance to skilled attackers using penetration testing.**

### Article 53 — Conformity self-assessment

1. A scheme may allow conformity self-assessment under the sole responsibility of the manufacturer/provider — **permitted only for products presenting a low risk corresponding to assurance level 'basic'.**

2. The manufacturer/provider may issue an **EU statement of conformity**, assuming responsibility for compliance.

3. Technical documentation and the EU statement of conformity must be made available to the national cybersecurity certification authority for the retention period specified in the scheme; a copy of the EU statement of conformity is submitted to that authority and to ENISA.

4. Issuing an EU statement of conformity is **voluntary, unless otherwise specified in Union or Member State law.**

5. EU statements of conformity are recognised in all Member States.

### Article 54 — Elements of European cybersecurity certification schemes

A scheme must include (non-exhaustive selection of the 22-point list at Art. 54(1)): subject matter and scope; purpose and how standards/evaluation methods/assurance levels meet user needs; references to applicable standards or technical specifications; the assurance level(s) applicable; whether self-assessment is permitted; specific requirements for conformity assessment bodies; evaluation criteria and methods; rules on marks/labels; rules on monitoring continued compliance; certificate issuance/maintenance/renewal conditions; consequences of non-compliant certified products; vulnerability-reporting rules; record-retention rules for conformity assessment bodies; content/format of certificates and EU statements of conformity; retention period for supporting documentation; maximum validity period of certificates; disclosure policy; mutual-recognition conditions with third countries; peer-assessment mechanism rules (Art. 56(6)).

3. Where specific Union legal acts so provide, a certificate or EU statement of conformity issued under a scheme **may be used to demonstrate presumption of conformity** with that legal act's requirements — the mechanism by which a future EUCC-style certificate could interact with CRA/RED-style presumption of conformity, if such a cross-reference is ever legislated.

### Article 55 — Supplementary cybersecurity information

Manufacturers/providers of certified products (or products with an EU statement of conformity) must publicly disclose: secure-configuration/deployment/maintenance guidance; the security-support period, particularly for cybersecurity updates; vulnerability-reporting contact information; links to public vulnerability repositories and relevant advisories. This information must remain available and updated at least until certificate/statement expiry.

### Article 56 — Cybersecurity certification

1. Certified products are presumed to comply with the requirements of the scheme under which they were certified.

2. **Cybersecurity certification is voluntary, unless otherwise specified by Union or Member State law.**

3. The Commission regularly assesses (first by 31 December 2023, then at least every two years) whether a specific scheme should be made **mandatory** through relevant Union law, prioritising the sectors listed in Annex II to Directive (EU) 2016/1148 (the original NIS Directive's critical-sector list). Assessment factors include cost/benefit impact on manufacturers and users, existing Member State/third-country law, open stakeholder consultation, implementation deadlines/transitional measures (with SME impact considered), and the most efficient path from voluntary to mandatory.

4. Conformity assessment bodies (Art. 60) issue certificates at 'basic' or 'substantial' assurance levels.

5. By derogation, in duly justified cases a scheme may require that certificates be issued **only by a public body** — either the national cybersecurity certification authority itself, or a public body accredited as a conformity assessment body.

6. For **assurance level 'high'**, certificates may only be issued by the national cybersecurity certification authority, or by a conformity assessment body **with prior approval per certificate** or under a **general delegation** from that authority.

7–10. The applicant must supply all information necessary for certification; certificate holders must report subsequently detected vulnerabilities/irregularities to the issuing authority/body, which forwards this to the national cybersecurity certification authority; certificates are issued for the scheme-specified period and may be renewed; certificates are recognised across all Member States.

### Article 57 — National cybersecurity certification schemes and certificates

National schemes covering products already covered by an adopted European scheme cease to have effect from the date set in the relevant implementing act (Art. 49(7)); Member States cannot introduce new national schemes overlapping an existing European one; certificates already issued nationally remain valid until expiry; Member States must inform the Commission and ECCG of any intention to draw up new national schemes (to avoid fragmentation).

### Article 58 — National cybersecurity certification authorities

Each Member State designates one or more national cybersecurity certification authorities, independent of the entities they supervise in organisation, funding, legal structure and decision-making (Art. 58(3)); certificate-issuance activities must be strictly separated from supervisory activities (Art. 58(4)). Tasks (Art. 58(7)) include: supervising/enforcing scheme compliance; monitoring manufacturers/providers doing self-assessment; assisting national accreditation bodies; monitoring public bodies issuing certificates; authorising conformity assessment bodies; handling complaints; annual reporting to ENISA/ECCG; cooperating with other national authorities. Powers (Art. 58(8)) include requesting information, carrying out audits, taking corrective measures, accessing premises for investigations, **withdrawing non-compliant certificates**, and **imposing penalties per Article 65.**

### Article 59 — Peer review

National cybersecurity certification authorities are subject to peer review by at least two other Member States' authorities plus the Commission, at least once every five years, assessing separation of issuance/supervisory functions, compliance-monitoring procedures, and staff expertise for 'high' assurance level authorities. ENISA may participate.

### Article 60 — Conformity assessment bodies

Conformity assessment bodies must be **accredited by national accreditation bodies** under Regulation (EC) No 765/2008, meeting the requirements in the Annex to this Regulation. Where a national cybersecurity certification authority itself issues certificates, its certification body must also be accredited. Accreditation is issued for a **maximum of five years**, renewable if requirements continue to be met; national accreditation bodies must restrict/suspend/revoke accreditation where conditions are no longer met.

### Article 61 — Notification

National authorities notify the Commission of accredited (and, where applicable, authorised) conformity assessment bodies per scheme and assurance level; the Commission publishes the list in the Official Journal one year after a scheme's entry into force, with subsequent amendments published within one to two months of notification.

### Article 62 — European Cybersecurity Certification Group (ECCG)

Composed of representatives of national cybersecurity certification authorities (one member per authority, max. two Member States represented per member). Tasks include advising/assisting the Commission on Title III implementation and the rolling work programme; assisting ENISA on candidate schemes; adopting opinions on candidate and existing schemes; requesting ENISA to prepare candidate schemes; facilitating cooperation and capacity-building among national authorities; supporting peer-assessment mechanisms; facilitating alignment with international standards. Chaired by the Commission with ENISA's assistance.

### Article 63 — Right to lodge a complaint

Natural/legal persons may lodge complaints with the certificate issuer, or with the relevant national cybersecurity certification authority where a conformity assessment body issued the certificate under Art. 56(6).

### Article 64 — Right to an effective judicial remedy

Right to judicial remedy regarding decisions on certificate issuance/refusal/recognition, or failure to act on a complaint — proceedings brought before the courts of the Member State where the relevant authority/body is located.

### Article 65 — Penalties

**Member States lay down the rules on penalties** applicable to infringements of Title III and of European cybersecurity certification schemes — penalties must be "effective, proportionate and dissuasive." **No EU-wide fixed fine figure is set**, structurally similar to RED's Article 46 and unlike the CRA's Article 64 (see [`../red/penalties-enforcement.md`](../red/penalties-enforcement.md) for that comparison).

# TITLE IV — FINAL PROVISIONS

### Article 66 — Committee procedure

The Commission is assisted by a committee under Regulation (EU) No 182/2011 (examination procedure).

### Article 67 — Evaluation and review

By 28 June 2024 and every five years thereafter, the Commission evaluates ENISA's impact/effectiveness/efficiency and the Title III certification framework's impact on internal-market functioning, including **whether essential cybersecurity requirements for market access are necessary** to keep non-compliant ICT products, services and processes out of the Union market (Art. 67(3)) — a provision worth noting since the CRA later did introduce exactly such essential requirements for products with digital elements.

### Article 68 — Repeal and succession

Regulation (EU) No 526/2013 is repealed from 27 June 2019; ENISA under this Regulation succeeds ENISA as previously established, inheriting ownership, agreements, obligations, contracts and liabilities. ENISA is established for an indefinite period from 27 June 2019.

### Article 69 — Entry into force

1. This Regulation entered into force on the twentieth day following its publication in the Official Journal.

2. **Articles 58, 60, 61, 63, 64 and 65 applied from 28 June 2021** — i.e., the national-authority, accreditation, notification, complaint, judicial-remedy and penalty provisions had a delayed application date relative to the rest of the Regulation.

---

# ANNEX — Requirements to be met by conformity assessment bodies

Conformity assessment bodies that wish to be accredited shall meet the following requirements:

1. Established under national law, with legal personality.

2. A **third-party body independent** of the organisation or the ICT products/services/processes it assesses.

3. A body belonging to a business association or professional federation may still qualify as a conformity assessment body if its independence and absence of conflict of interest are demonstrated.

4. The body, its top-level management, and staff responsible for conformity assessment tasks must **not be** the designer, manufacturer, supplier, installer, purchaser, owner, user or maintainer of the assessed product/service/process, or their authorised representative (this does not preclude using assessed products for the body's own operations or personal use).

5. They must **not be directly involved** in the design, manufacture, marketing, installation, use or maintenance of what is assessed, nor represent parties engaged in those activities, nor engage in any activity conflicting with independence of judgement or integrity — **this prohibition applies in particular to consultancy services.**

6. Where a conformity assessment body is owned/operated by a public entity, independence and absence of conflict of interest between the national cybersecurity certification authority and the body must be ensured and documented.

7. Subsidiaries' and subcontractors' activities must not affect confidentiality, objectivity or impartiality.

8. Staff must act with the highest professional integrity and requisite technical competence, free from pressures/inducements (including financial) that might influence judgement or results.

9. The body must be capable of carrying out all assigned conformity assessment tasks itself or via properly documented, written-agreement-governed subcontracting/consultation (no intermediaries) — while retaining full responsibility.

10. For each conformity assessment procedure and product/service/process type, the body must have: (a) technically knowledgeable and experienced staff; (b) documented, reproducible assessment procedures, with policies distinguishing notified-body tasks (Art. 61) from other activities; (c) procedures accounting for undertaking size, sector, structure, technological complexity, and production scale.

11. Necessary means for technical/administrative tasks, plus access to all necessary equipment and facilities.

12. Persons carrying out assessments must have: (a) sound technical/vocational training; (b) satisfactory knowledge of and adequate authority for the assessments they perform; (c) appropriate knowledge of applicable requirements and testing standards; (d) ability to draw up certificates, records and reports demonstrating assessments were carried out.

13. Impartiality of the body, its management, assessment staff and subcontractors must be **guaranteed**.

14. **Remuneration of top-level management and assessment staff must not depend on the number or results of assessments carried out.**

15. Conformity assessment bodies must take out **liability insurance**, unless liability is assumed by the Member State or the Member State is itself directly responsible for the assessment.

16. Confidentiality/professional secrecy obligations apply to the body, its staff, committees, subsidiaries, subcontractors and associated bodies for all information obtained in carrying out assessment tasks, except where Union/Member State law requires disclosure or in dealings with the competent national authorities; intellectual property rights must be protected; documented procedures required.

17. Subject to point 16, this Annex does not preclude technical/regulatory-guidance exchanges between a conformity assessment body and an applicant or prospective applicant.

18. Bodies must operate under **consistent, fair and reasonable terms and conditions, taking into account SME interests regarding fees.**

19. Bodies must meet the relevant harmonised standard under Regulation (EC) No 765/2008 for accreditation of certification bodies for ICT products/services/processes.

20. Bodies must ensure that any testing laboratories they use meet the relevant harmonised standard under Regulation (EC) No 765/2008 for accreditation of testing laboratories.
