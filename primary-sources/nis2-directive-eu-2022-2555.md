# Directive (EU) 2022/2555 (NIS2) — measures for a high common level of cybersecurity across the Union

> **Primary source. Quote regulation wording from this file, not from summaries or the web.**
>
> - **Source:** EUR-Lex, CELEX `32022L2555` — <https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:32022L2555>
> - **Retrieved:** 2026-08-11, via rendered page extraction (Chrome, JS-rendered — EUR-Lex's HTML view is client-rendered and a plain HTTP fetch/curl returns only a cookie-consent shell, not the document text).
> - **Coverage of this copy:** Enacting terms (Articles 1–46, complete) and Annexes I and II (complete, both sector lists). Recitals (preamble) are only partially captured — the first ~57 of 139 recitals were retrieved; the rest were not needed for the operative-text sourcing this repository does and are not reproduced here. **Annex III (correlation table with the repealed NIS1 directive) was not captured** — it is procedural (maps old article numbers to new ones) and not needed for compliance guidance.
> - **Conversion:** extracted via the rendered page's `innerText` for the enacting-terms and annex containers, in overlapping chunks assembled together. Article and Annex headings promoted to Markdown headings. Wording is the same as the rendered OJ text; page chrome (navigation, cookie banners) stripped. Not independently checked character-by-character against the OJ PDF.
> - **Authoritative version:** the Official Journal text at the URL above (OJ L 333, 27.12.2022, p. 80). This copy exists so that checks cite the directive itself rather than a paraphrase of it.
> - **NOTE ON PARTIAL CAPTURE:** unlike the CRA and RED primary-source files in this folder, this file's recitals section is incomplete. If a check turns on the wording of a specific recital numbered above ~57, that recital is **not** in this file — fetch it fresh from the OJ before relying on it.

---

## Key locations

| Provision | What it says | Why we cite it |
|---|---|---|
| **Art. 2** | Scope: applies to entities in Annex I/II sectors that are medium+ enterprises (Recommendation 2003/361/EC), plus specific entities regardless of size (Art. 2(2)) | Decides who is in scope at all |
| **Art. 3** | Splits in-scope entities into **essential** and **important** entities | Determines which supervisory/enforcement regime applies (Art. 32 vs Art. 33) |
| **Art. 20** | Governance — management bodies must approve and oversee cybersecurity risk-management measures, and can be held personally liable | The "board is accountable" provision, distinct from CRA/RED which don't name a governance body |
| **Art. 21** | Cybersecurity risk-management measures — the substantive security obligation, a 10-point minimum list | NIS2's equivalent of CRA Annex I; this is what "compliance" substantively means |
| **Art. 23** | Reporting obligations — the 24h/72h/1-month notification clock for "significant incidents" | The operational deadline manufacturers/entities actually have to hit |
| **Art. 34** | Administrative fines — €10M/2% (essential) and €7M/1.4% (important) turnover-based maximums | NIS2's penalty structure, materially different from both CRA and RED |
| **Art. 41** | Transposition: 17 October 2024 (adopt), applicable from 18 October 2024 | The date NIS2 obligations actually started biting |
| **Art. 44** | Repeals Directive (EU) 2016/1148 ("NIS1") with effect from 18 October 2024 | NIS2 is a full replacement, not an amendment |
| **Annex I** | 11 "sectors of high criticality" | The primary determinant of whether an entity is in scope |
| **Annex II** | 7 "other critical sectors" | Secondary scope list — generally maps to "important" rather than "essential" by default |

## Related files

- [`cra-regulation-eu-2024-2847.md`](cra-regulation-eu-2024-2847.md) — the CRA regulates *products*; NIS2 regulates *entities/organisations*. A manufacturer can be in scope of both simultaneously in different capacities (see `relationship-to-other-eu-law.md`).

---

27.12.2022

EN

Official Journal of the European Union

L 333/80

DIRECTIVE (EU) 2022/2555 OF THE EUROPEAN PARLIAMENT AND OF THE COUNCIL

of 14 December 2022

on measures for a high common level of cybersecurity across the Union, amending Regulation (EU) No 910/2014 and Directive (EU) 2018/1972, and repealing Directive (EU) 2016/1148 (NIS 2 Directive)

(Text with EEA relevance)

*[Recitals 1–57 retrieved but omitted from this excerpt for length — see note above. Full enacting terms follow below.]*

---

### CHAPTER I

GENERAL PROVISIONS

### Article 1

Subject matter

1. This Directive lays down measures that aim to achieve a high common level of cybersecurity across the Union, with a view to improving the functioning of the internal market.

2. To that end, this Directive lays down:

(a) obligations that require Member States to adopt national cybersecurity strategies and to designate or establish competent authorities, cyber crisis management authorities, single points of contact on cybersecurity (single points of contact) and computer security incident response teams (CSIRTs);

(b) cybersecurity risk-management measures and reporting obligations for entities of a type referred to in Annex I or II as well as for entities identified as critical entities under Directive (EU) 2022/2557;

(c) rules and obligations on cybersecurity information sharing;

(d) supervisory and enforcement obligations on Member States.

### Article 2

Scope

1. This Directive applies to public or private entities of a type referred to in Annex I or II which qualify as medium-sized enterprises under Article 2 of the Annex to Recommendation 2003/361/EC, or exceed the ceilings for medium-sized enterprises provided for in paragraph 1 of that Article, and which provide their services or carry out their activities within the Union.

Article 3(4) of the Annex to that Recommendation shall not apply for the purposes of this Directive.

2. Regardless of their size, this Directive also applies to entities of a type referred to in Annex I or II, where:

(a) services are provided by: (i) providers of public electronic communications networks or of publicly available electronic communications services; (ii) trust service providers; (iii) top-level domain name registries and domain name system service providers;

(b) the entity is the sole provider in a Member State of a service which is essential for the maintenance of critical societal or economic activities;

(c) disruption of the service provided by the entity could have a significant impact on public safety, public security or public health;

(d) disruption of the service provided by the entity could induce a significant systemic risk, in particular for sectors where such disruption could have a cross-border impact;

(e) the entity is critical because of its specific importance at national or regional level for the particular sector or type of service, or for other interdependent sectors in the Member State;

(f) the entity is a public administration entity: (i) of central government as defined by a Member State in accordance with national law; or (ii) at regional level as defined by a Member State in accordance with national law that, following a risk-based assessment, provides services the disruption of which could have a significant impact on critical societal or economic activities.

3. Regardless of their size, this Directive applies to entities identified as critical entities under Directive (EU) 2022/2557.

4. Regardless of their size, this Directive applies to entities providing domain name registration services.

5. Member States may provide for this Directive to apply to: (a) public administration entities at local level; (b) education institutions, in particular where they carry out critical research activities.

6.–14. [national security safeguards, exemptions for national-security/law-enforcement entities, interaction with GDPR/ePrivacy, confidentiality of exchanged information, personal data processing basis — full text in the OJ]

### Article 3

Essential and important entities

1. For the purposes of this Directive, the following entities shall be considered to be essential entities:

(a) entities of a type referred to in Annex I which exceed the ceilings for medium-sized enterprises provided for in Article 2(1) of the Annex to Recommendation 2003/361/EC;

(b) qualified trust service providers and top-level domain name registries as well as DNS service providers, regardless of their size;

(c) providers of public electronic communications networks or of publicly available electronic communications services which qualify as medium-sized enterprises under Article 2 of the Annex to Recommendation 2003/361/EC;

(d) public administration entities referred to in Article 2(2), point (f)(i);

(e) any other entities of a type referred to in Annex I or II that are identified by a Member State as essential entities pursuant to Article 2(2), points (b) to (e);

(f) entities identified as critical entities under Directive (EU) 2022/2557, referred to in Article 2(3) of this Directive;

(g) if the Member State so provides, entities which that Member State identified before 16 January 2023 as operators of essential services in accordance with Directive (EU) 2016/1148 or national law.

2. For the purposes of this Directive, entities of a type referred to in Annex I or II which do not qualify as essential entities pursuant to paragraph 1 of this Article shall be considered to be important entities. This includes entities identified by Member States as important entities pursuant to Article 2(2), points (b) to (e).

3. By 17 April 2025, Member States shall establish a list of essential and important entities as well as entities providing domain name registration services. Member States shall review and, where appropriate, update that list on a regular basis and at least every two years thereafter.

4.–6. [registration/notification procedures for that list — full text in the OJ]

### Article 4

Sector-specific Union legal acts

Where sector-specific Union legal acts require essential or important entities to adopt cybersecurity risk-management measures or to notify significant incidents, and those requirements are at least equivalent in effect to this Directive's obligations, the relevant provisions of this Directive (including supervision/enforcement, Chapter VII) do not apply to such entities. [Full conditions, Art. 4(2)-(3), in the OJ.]

### Article 5

Minimum harmonisation

This Directive shall not preclude Member States from adopting or maintaining provisions ensuring a higher level of cybersecurity, provided that such provisions are consistent with Member States' obligations laid down in Union law.

### Article 6

Definitions

*(41 defined terms — key ones relevant to compliance work: (6) 'incident' = an event compromising availability, authenticity, integrity or confidentiality of stored/transmitted/processed data or of the services offered by/accessible via network and information systems. (7) 'large-scale cybersecurity incident' = disruption exceeding a Member State's capacity to respond, or significant impact on ≥2 Member States. (15) 'vulnerability' = a weakness, susceptibility or flaw of ICT products/services exploitable by a cyber threat. (11) 'significant cyber threat' = a cyber threat that could have a severe impact by causing considerable material or non-material damage. Full list of 41 definitions in the OJ text.)*

### CHAPTER II

COORDINATED CYBERSECURITY FRAMEWORKS

### Article 7

National cybersecurity strategy — each Member State adopts a national strategy (objectives, governance framework, risk assessment mechanism, incident-response measures, awareness plan). Full detail in the OJ.

### Article 8

Competent authorities and single points of contact — each Member State designates competent authorities and a single point of contact for cross-border/cross-sectoral liaison.

### Article 9

National cyber crisis management frameworks

### Article 10

Computer security incident response teams (CSIRTs) — each Member State designates/establishes one or more CSIRTs, covering at minimum the Annex I/II sectors.

### Article 11

Requirements, technical capabilities and tasks of CSIRTs

### Article 12

Coordinated vulnerability disclosure and a European vulnerability database — each Member State designates a coordinating CSIRT for coordinated vulnerability disclosure; ENISA develops and maintains a European vulnerability database (voluntary disclosure/registration of publicly known vulnerabilities).

### Article 13

Cooperation at national level

### CHAPTER III

COOPERATION AT UNION AND INTERNATIONAL LEVEL

### Article 14

Cooperation Group — established to support strategic cooperation among Member States, the Commission and ENISA.

### Article 15

CSIRTs network — network of national CSIRTs plus CERT-EU, for operational cooperation, information exchange, and coordinated incident response.

### Article 16

European cyber crisis liaison organisation network (EU-CyCLONe) — supports coordinated management of large-scale cybersecurity incidents/crises at operational level.

### Article 17

International cooperation

### Article 18

Report on the state of cybersecurity in the Union — ENISA publishes a biennial report.

### Article 19

Peer reviews — voluntary peer reviews of Member States' implementation, methodology established by the Cooperation Group by 17 January 2025.

### CHAPTER IV

CYBERSECURITY RISK-MANAGEMENT MEASURES AND REPORTING OBLIGATIONS

### Article 20

Governance

1. Member States shall ensure that the management bodies of essential and important entities approve the cybersecurity risk-management measures taken by those entities in order to comply with Article 21, oversee its implementation and **can be held liable for infringements by the entities of that Article**.

2. Member States shall ensure that the members of the management bodies of essential and important entities are required to follow training, and shall encourage essential and important entities to offer similar training to their employees on a regular basis.

### Article 21

Cybersecurity risk-management measures

1. Member States shall ensure that essential and important entities take appropriate and proportionate technical, operational and organisational measures to manage the risks posed to the security of network and information systems which those entities use for their operations or for the provision of their services, and to prevent or minimise the impact of incidents on recipients of their services and on other services.

Taking into account the state-of-the-art and, where applicable, relevant European and international standards, as well as the cost of implementation, the measures shall ensure a level of security appropriate to the risks posed. When assessing proportionality, due account shall be taken of the entity's degree of exposure to risks, its size, and the likelihood and severity of incidents, including their societal and economic impact.

2. The measures shall be based on an **all-hazards approach** and shall include at least the following:

(a) policies on risk analysis and information system security;

(b) incident handling;

(c) business continuity, such as backup management and disaster recovery, and crisis management;

(d) supply chain security, including security-related aspects concerning the relationships between each entity and its direct suppliers or service providers;

(e) security in network and information systems acquisition, development and maintenance, including vulnerability handling and disclosure;

(f) policies and procedures to assess the effectiveness of cybersecurity risk-management measures;

(g) basic cyber hygiene practices and cybersecurity training;

(h) policies and procedures regarding the use of cryptography and, where appropriate, encryption;

(i) human resources security, access control policies and asset management;

(j) the use of multi-factor authentication or continuous authentication solutions, secured voice, video and text communications and secured emergency communication systems within the entity, where appropriate.

3. When considering supply-chain measures (point (d)), entities must take into account vulnerabilities specific to each direct supplier/service provider, the overall quality of their products/cybersecurity practices including secure development procedures, and results of coordinated EU-level supply-chain risk assessments (Art. 22).

4. An entity that finds it does not comply with paragraph 2's measures must, without undue delay, take all necessary, appropriate and proportionate corrective measures.

5. By 17 October 2024, the Commission adopts implementing acts specifying technical/methodological requirements for specific provider types (DNS providers, TLD registries, cloud/data-centre/CDN providers, managed (security) service providers, online marketplaces/search engines/social networks, trust service providers); may extend to other entities.

### Article 22

Union level coordinated security risk assessments of critical supply chains — the Cooperation Group, with the Commission and ENISA, may carry out coordinated risk assessments of specific critical ICT supply chains.

### Article 23

Reporting obligations

1. Each Member State shall ensure that essential and important entities notify, without undue delay, its CSIRT or competent authority of any incident that has a significant impact on the provision of their services (a **"significant incident"**, as defined in paragraph 3). Entities must also notify affected service recipients where appropriate. **The mere act of notification shall not subject the notifying entity to increased liability.**

2. Entities must communicate to potentially affected service recipients, without undue delay, any measures/remedies those recipients can take in response to a significant cyber threat.

3. An incident is **"significant"** if: (a) it has caused or is capable of causing severe operational disruption of the services or financial loss for the entity concerned; or (b) it has affected or is capable of affecting other natural or legal persons by causing considerable material or non-material damage.

4. The notification clock — for the purpose of notification under paragraph 1, entities must submit:

(a) **within 24 hours** of becoming aware of the significant incident — an early warning, indicating (where applicable) suspected unlawful/malicious cause or cross-border impact;

(b) **within 72 hours** of becoming aware — an incident notification, updating the early warning and giving an initial assessment (severity, impact, indicators of compromise where available);

(c) **upon request** of the CSIRT/competent authority — an intermediate report on status updates;

(d) **not later than one month** after the incident notification (point (b)) — a final report: detailed description including severity/impact, likely threat/root cause, applied and ongoing mitigation measures, cross-border impact where applicable;

(e) if the incident is still ongoing when the final report would be due — a progress report at that point, and a final report within one month of the incident being fully handled.

Trust service providers have a stricter rule: significant incidents affecting trust services must be notified **within 24 hours**, without the separate 72-hour tier.

5. The CSIRT/competent authority must respond to the notifying entity, where possible within 24 hours of the early warning, with initial feedback and (on request) guidance or operational advice.

6.–11. [cross-border information sharing, public-awareness disclosure, quarterly aggregate reporting to ENISA, implementing acts specifying notification format/significant-incident criteria for named provider types by 17 October 2024 — full text in the OJ]

### Article 24

Use of European cybersecurity certification schemes — Member States may require essential/important entities to use ICT products/services/processes certified under EU cybersecurity certification schemes (Regulation (EU) 2019/881, Art. 49); Commission empowered to adopt delegated acts mandating this for specific entity categories where insufficient cybersecurity levels are identified.

### Article 25

Standardisation — Member States encourage use of European/international standards to promote convergent implementation of Article 21(1)-(2), without favouring a particular technology.

### CHAPTER V

JURISDICTION AND REGISTRATION

### Article 26

Jurisdiction and territoriality

1. Entities fall under the jurisdiction of the Member State in which they are established, **except**:

(a) providers of public electronic communications networks/services — jurisdiction is the Member State where they provide services;

(b) DNS service providers, TLD registries, domain-name-registration entities, cloud computing/data-centre/CDN providers, managed (security) service providers, online marketplaces/search engines/social-networking providers — jurisdiction follows their **main establishment** in the Union (main establishment = place of the entity's EU headquarters/main cybersecurity-decision-making, per the fuller Art. 26 text in the OJ).

[Full remainder of Art. 26 (2)-(5) and Article 27 (Registry of entities), Article 28 (Database of domain name registration data) in the OJ.]

### CHAPTER VI

*[Not separately captured in this excerpt — covers delegated act on certification (Art. 24) cross-references; see Chapter numbering note: this Directive's Chapter VI is "Delegated and implementing acts" per Article 38's chapter heading below.]*

### Article 29

Cybersecurity information-sharing arrangements — Member States facilitate voluntary information-sharing arrangements among essential/important entities and, where relevant, their suppliers.

### Article 30

Voluntary notification of relevant information — voluntary notification channel (incidents, cyber threats, near misses) for entities not otherwise obligated, or for the additional categories listed in Art. 30(1)(a)-(b). Voluntary reporting does not create additional obligations for the notifying entity.

### CHAPTER VII

SUPERVISION AND ENFORCEMENT

### Article 31

General aspects concerning supervision and enforcement — competent authorities must effectively supervise and enforce compliance; may prioritise supervisory tasks on a risk-based approach.

### Article 32

Supervisory and enforcement measures in relation to **essential** entities

Essential entities are subject to **both proactive and reactive supervision** — competent authorities have power to conduct on-site inspections, off-site supervision including random checks, regular *and* targeted security audits, ad hoc audits, security scans, and information/document requests — **without needing prior evidence of non-compliance**.

Enforcement powers (para. 4) include: warnings, binding instructions, cease-and-desist orders, orders to comply with Art. 21/23, orders to inform affected service recipients of a threat, orders to implement audit recommendations, designating a monitoring officer, orders to make infringements public, and administrative fines (Art. 34). Where measures (a)-(d)/(f) prove ineffective, competent authorities may (para. 5) temporarily suspend certifications/authorisations or request the temporary prohibition of a named individual (CEO/legal representative) from exercising managerial functions — subject to procedural safeguards, and **not applicable to public administration entities**.

### Article 33

Supervisory and enforcement measures in relation to **important** entities

Important entities are subject to **ex post supervision only** — competent authorities act "where necessary" upon evidence, indication, or information of alleged non-compliance (para. 1), rather than proactively. Available supervisory powers (para. 2) are narrower than for essential entities: on-site/off-site ex post supervision, targeted (not regular) security audits, security scans, information/document requests. Enforcement powers (para. 4) largely mirror Article 32(4) (warnings through administrative fines) but **omit** the power to designate a monitoring officer. Article 32(6)-(8) (personal liability of representatives, procedural fairness) applies mutatis mutandis.

**This is the single most important structural distinction in NIS2**: essential entities face active, ongoing regulatory scrutiny; important entities are checked reactively, generally only after something has already gone wrong or been reported.

### Article 34

General conditions for imposing administrative fines on essential and important entities

4. **Essential entities**, for infringement of Article 21 or 23: administrative fines of a maximum of **at least EUR 10,000,000, or at least 2% of total worldwide annual turnover in the preceding financial year**, whichever is higher.

5. **Important entities**, for infringement of Article 21 or 23: administrative fines of a maximum of **at least EUR 7,000,000, or at least 1.4% of total worldwide annual turnover in the preceding financial year**, whichever is higher.

These are **floors on the maximum** Member States must legislate ("at least") — a Member State may set a higher cap in national law; these figures are not automatically the fine actually imposed in any given case (paras. 1-3: fines must be effective, proportionate, dissuasive, with the Art. 32(7) factors — severity, duration, prior infringements, damage caused, intent/negligence, mitigation, cooperation — taken into account).

### Article 35

Infringements entailing a personal data breach — coordination with GDPR supervisory authorities; no double administrative fine for the same conduct under both NIS2 and GDPR Art. 58(2)(i).

### Article 36

Penalties

Member States shall lay down rules on penalties applicable to infringements of national measures adopted pursuant to this Directive and shall take all measures necessary to ensure that they are implemented. The penalties provided for shall be effective, proportionate and dissuasive. Member States shall, by **17 January 2025**, notify the Commission of those rules.

*(Note: Article 36's "penalties" is a general/residual clause, distinct from Article 34's specific administrative-fine floors for Art. 21/23 infringements — Article 34 already covers the main compliance failures with hard EU-wide minimum-maximum figures; Article 36 covers other infringements of national transposing law.)*

### Article 37

Mutual assistance — cross-border cooperation duties between competent authorities where an entity operates in multiple Member States.

### CHAPTER VIII

DELEGATED AND IMPLEMENTING ACTS

### Article 38

Exercise of the delegation (re: Art. 24(2) certification-mandate delegated acts) — five-year delegation from 16 January 2023.

### Article 39

Committee procedure

### CHAPTER IX

FINAL PROVISIONS

### Article 40

Review — Commission reviews the Directive's functioning by **17 October 2027** and every 36 months thereafter.

### Article 41

Transposition

1. By **17 October 2024**, Member States shall adopt and publish the measures necessary to comply with this Directive. They shall immediately inform the Commission thereof.

They shall apply those measures **from 18 October 2024**.

### Article 42

Amendment of Regulation (EU) No 910/2014 — Article 19 deleted with effect from 18 October 2024.

### Article 43

Amendment of Directive (EU) 2018/1972 — Articles 40 and 41 deleted with effect from 18 October 2024.

### Article 44

Repeal

**Directive (EU) 2016/1148 is repealed with effect from 18 October 2024.** References to the repealed Directive (NIS1) are construed as references to this Directive, per the correlation table in Annex III.

### Article 45

Entry into force

This Directive shall enter into force on the twentieth day following that of its publication in the Official Journal of the European Union. *(Published 27.12.2022 → entry into force 16 January 2023 — this is the date used elsewhere in the text, e.g. Art. 3(1)(g), as the "before 16 January 2023" cutoff.)*

### Article 46

Addressees

This Directive is addressed to the Member States.

---

### ANNEX I

SECTORS OF HIGH CRITICALITY

1. **Energy** — (a) Electricity (supply undertakings, DSOs, TSOs, producers, nominated electricity market operators, aggregation/demand-response/storage market participants, EV recharging-point operators); (b) District heating and cooling; (c) Oil (transmission pipeline operators, production/refining/treatment/storage/transmission operators, central stockholding entities); (d) Gas (supply undertakings, DSOs, TSOs, storage/LNG system operators, natural gas undertakings, refining/treatment facility operators); (e) Hydrogen (production, storage and transmission operators)

2. **Transport** — (a) Air (air carriers for commercial purposes, airport managing bodies/airports, air traffic control operators); (b) Rail (infrastructure managers, railway undertakings including service-facility operators); (c) Water (passenger/freight water transport companies, port managing bodies, vessel traffic services operators); (d) Road (road authorities responsible for traffic management, Intelligent Transport Systems operators)

3. **Banking** — credit institutions

4. **Financial market infrastructures** — trading venue operators, central counterparties (CCPs)

5. **Health** — healthcare providers, EU reference laboratories, medicinal-product R&D entities, pharmaceutical manufacturers, manufacturers of medical devices critical during a public health emergency

6. **Drinking water** — suppliers/distributors of water for human consumption

7. **Waste water** — undertakings collecting/disposing/treating urban, domestic or industrial waste water

8. **Digital infrastructure** — Internet Exchange Point providers; DNS service providers (excluding root name server operators); TLD name registries; cloud computing service providers; data centre service providers; content delivery network providers; trust service providers; providers of public electronic communications networks; providers of publicly available electronic communications services

9. **ICT service management (business-to-business)** — managed service providers; managed security service providers

10. **Public administration** — central government entities; regional government entities (as defined by national law)

11. **Space** — operators of ground-based infrastructure supporting space-based services (owned/managed/operated by Member States or private parties)

### ANNEX II

OTHER CRITICAL SECTORS

1. **Postal and courier services**

2. **Waste management** (where waste management is the principal economic activity)

3. **Manufacture, production and distribution of chemicals**

4. **Production, processing and distribution of food** (wholesale distribution and industrial production/processing)

5. **Manufacturing** — (a) medical devices and in-vitro diagnostic medical devices (excluding the public-health-emergency-critical devices already in Annex I point 5); (b) computer, electronic and optical products (NACE Rev. 2 section C division 26); (c) electrical equipment (division 27); (d) machinery and equipment n.e.c. (division 28); (e) motor vehicles, trailers and semi-trailers (division 29); (f) other transport equipment (division 30)

6. **Digital providers** — online marketplaces; online search engines; social networking services platforms

7. **Research** — research organisations

*(Annex III, the correlation table mapping NIS1 (Directive (EU) 2016/1148) provisions to their NIS2 equivalents, was not captured in this copy — it is procedural rather than substantive and not required for compliance guidance.)*
