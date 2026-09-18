**Analysis of how the Cyber Resilience Act (Regulation (EU) 2024/2847) interacts with EU law**

The adoption of Regulation (EU) 2024/2847 on horizontal cybersecurity requirements for products with digital elements, known as the Cyber Resilience Act (CRA), forms a foundational legal layer for protecting the EU digital market. The CRA sets mandatory requirements for the design, development, production, and maintenance of software and hardware throughout its entire lifecycle.

The CRA's rollout is coordinated with existing EU law through three key interaction mechanisms:

- **Overlaps**: shares common legal ground with acts where functional obligations, reporting procedures, and market surveillance need to be aligned.

- **Excludes**: fully removes certain categories of specialised products from its scope in favour of the relevant sector-specific legislation.

- **Complements**: operates in parallel with other acts, providing a baseline technical level of cyber protection that supports the goals of broader legal regulation.

The table below summarises how the CRA relates to other key EU regulatory acts.

| **EU regulatory act** | **Nature of interaction** | **Legal basis and mechanism** | **Main regulatory focus** |
| --- | --- | --- | --- |
| **NIS2 Directive (EU) 2022/2555** | Overlaps | NIS2 — Art. 21, 23; CRA — Art. 14, 54 | NIS2 regulates entities; CRA regulates products |
| **RED Directive 2014/53/EU + Regulation 2022/30** | Overlaps and is repealed in favour of CRA | Repeal of Regulation (EU) 2022/30 from 11.12.2027 | Replacing radio-equipment-specific requirements with the CRA framework |
| **AI Act (EU) 2024/1689** | Overlaps and complements | CRA — Art. 12; AI Act — Art. 15 | Cybersecurity for high-risk AI products |
| **Machinery Regulation (EU) 2023/1230** | Overlaps and complements | Integration of conformity assessment and single declaration | Functional machine safety and software cyber protection |
| **Medical Devices Regulation (MDR) (EU) 2017/745** | Excludes | CRA — Art. 2(2)(a) | Full exclusion of medical devices from CRA scope |
| **Automotive regulations (UN R155, 2019/2144)** | Excludes | CRA — Art. 2(2)(c) | Full exclusion of vehicles from CRA scope |
| **GDPR (EU) 2016/679** | Complements | GDPR — Art. 32; CRA — Annex I | Technical support for data-processing security |
| **Cybersecurity Act (CSA) (EU) 2019/881** | Overlaps and complements | EUCC scheme under CSA; CRA — Art. 27, 32 | Certification gives a presumption of CRA conformity |

**NIS2 Directive (EU) 2022/2555: entity-level and product-level regulation working together**

**Nature of interaction: Overlaps.**

The NIS2 Directive and the CRA form the two main pillars of EU digital security, but their regulatory subject matter differs. NIS2 is entity-based regulation, setting requirements for cyber risk management, operational resilience, and incident reporting for organisations classified as "essential entities" or "important entities." The CRA, by contrast, is product-based regulation, directly governing products with digital elements (PDEs) and their development and support processes.

A direct overlap arises where a manufacturer simultaneously qualifies as an "important entity" under Annex II of NIS2 (for example, companies manufacturing computer, electronic, or optical products) and also develops and places products with digital elements on the EU market that fall within the CRA's scope.

In that case, the organisation faces a dual regulatory burden requiring a clear separation of internal control procedures across three main areas:

1. **Risk and supply-chain management**:

  - Under Article 21(2)(d) of NIS2, an important entity must ensure the security of its own supply chain and its relationships with direct suppliers when procuring IT services or equipment for its own use.

  - Under the CRA, that same entity, acting as a manufacturer, must exercise due diligence when integrating third-party components into its *product*, maintain a software bill of materials (SBOM), and ensure the absence of known vulnerabilities at the time the product is placed on the market.

2. **Parallel incident-notification obligations**:

  - Under Article 23 of NIS2, an organisation must notify the national CSIRT or competent authority of any significant operational incident affecting the delivery of its *own services* or the operation of its internal infrastructure (with an early warning submitted within 24 hours).

  - Under Article 14 of the CRA (applies from 11 September 2026), a manufacturer must notify the coordinating CSIRT and ENISA, through the Single Reporting Platform, of any actively exploited vulnerability found in its *manufactured product*, as well as severe incidents affecting that product's security (also within 24 hours).

3. **Institutional cooperation between supervisory authorities**:

  - Articles 54–55 of the CRA require CRA market surveillance authorities to cooperate and exchange information regularly with the competent authorities designated under NIS2. If a market surveillance authority finds that a product with digital elements contains a critical vulnerability threatening the security of NIS2 essential entities, this provides grounds for urgent restrictions or withdrawal of the product from the market across the whole Union.

**Radio Equipment Directive 2014/53/EU and Delegated Regulation (EU) 2022/30: regulatory transition and repeal**

**Nature of interaction: Overlaps and is repealed in favour of CRA.**

The Radio Equipment Directive (RED) 2014/53/EU was the original instrument for setting cybersecurity requirements for wireless devices in the EU, under Article 3(3), points (d), (e), and (f) (protection of networks from harm, protection of personal data, and prevention of fraud). To activate these requirements, the European Commission adopted Delegated Regulation (EU) 2022/30, covering internet-connected radio equipment, portable devices, baby monitors, and toys.

Because radio equipment, by its nature, falls within the definition of products with digital elements (PDEs), there is a direct overlap in subject matter. To avoid duplicate checks and double marking, EU legislation provides a clear procedure for replacing the regulatory regime.

**Important — this is not just a future prospect.** RED's cybersecurity requirements (Article 3(3)(d)(e)(f), detailed in Delegated Regulation (EU) 2022/30 as amended by (EU) 2023/2444) have been legally binding since **1 August 2025** — that is, already today, well before the CRA's full application in December 2027. For any connected device with a radio interface (Wi-Fi, Bluetooth, etc.), this is a real, binding obligation right now, running in parallel with the upcoming CRA requirements — not something that "kicks in" only once the transition to the CRA happens.

Delegated Regulation (EU) 2022/30 is due to be **fully repealed from 11 December 2027**.

The regulatory transition and the boundaries of when each act applies unfold as follows:

- **10 December 2024**: The CRA's official entry into force, starting the general transitional period for industry adaptation.

- **11 June 2026**: Chapter IV of the CRA (Articles 35–51) starts to apply, governing the procedures for notifying conformity assessment bodies.

- **11 September 2026**: Mandatory application of Article 14 of the CRA begins, on notifying discovered and actively exploited vulnerabilities in products.

- **11 December 2027**: Full application of the CRA's essential cybersecurity requirements and CE marking begins. At the same time, a dedicated European Commission delegated act takes effect, fully repealing Delegated Regulation (EU) 2022/30. References to RED's harmonised cybersecurity standards are removed from Implementing Decision (EU) 2022/2191.

The legal rationale for the repeal is that the essential cybersecurity requirements set out in Annex I of the CRA fully cover and absorb the risks previously regulated under Article 3(3) of the RED. After 11 December 2027, any assessment of radio equipment's compliance with cybersecurity requirements will be carried out exclusively under the CRA, while the RED will retain its focus on the effective use of the radio spectrum and electromagnetic compatibility.

**AI Act (EU) 2024/1689: coordination on high-risk systems**

**Nature of interaction: Overlaps and complements.**

Regulation (EU) 2024/1689 (the AI Act) sets a harmonised, risk-based approach to the development, market placement, and use of AI systems in the EU. A regulatory overlap arises for AI systems that are simultaneously products with digital elements (PDEs) and classified as "high-risk AI systems" under Article 6 and Annexes I/III of the AI Act.

Under Article 15 of the AI Act, high-risk AI systems must maintain an appropriate level of accuracy, robustness, and cybersecurity throughout their lifecycle. To avoid duplicating conformity assessment procedures, **Article 12 of the CRA** ("High-risk AI systems") sets out a dedicated coordination mechanism with the AI Act (Article 8 of the CRA is only mentioned in passing within Article 12(3) — it concerns the Commission's powers to certify critical products, not coordination with the AI Act as such):

1. **Presumption of conformity with the AI Act's cybersecurity requirements**:

  - If a product with digital elements that contains a high-risk AI system meets the CRA's essential cybersecurity requirements (Annex I), that product is automatically presumed to meet the cybersecurity requirements set out in Article 15 of the AI Act, to the extent those requirements are covered by the CRA assessment.

2. **Procedural integration and the Single EU Declaration of Conformity**:

  - Under **Article 28(3) of the CRA**, when a product with digital elements falls under several EU legal acts, each requiring its own declaration of conformity, manufacturers do not need to go through separate, isolated procedures for each regulation. The manufacturer draws up a Single EU Declaration of Conformity listing all applicable acts of EU harmonisation legislation, including the AI Act and the CRA. (Article 13(12) of the CRA simply directs the manufacturer to Article 28 for how to draw up the declaration.)

3. **Division of subject-matter competence**:

  - The CRA covers the product's general engineering cybersecurity (protection against unauthorised access, resilience of network interfaces, vulnerability management, and code security).

  - The AI Act complements these requirements by regulating threats specific to AI models: training-data poisoning, adversarial attacks, transparency of algorithmic decisions, and prevention of systemic model failures.

**Machinery Regulation (EU) 2023/1230: functional safety versus cyber protection**

**Nature of interaction: Overlaps and complements.**

Regulation (EU) 2023/1230 on machinery harmonises requirements for functional safety, health protection, and prevention of physical risk during the operation of machinery. Modern machinery is increasingly fitted with digital interfaces, sensor networks, wireless controls, and software.

Article 2 of the CRA contains no blanket exclusion for machinery. The interaction between Regulation 2023/1230 and the CRA is based on a clear division of protective scope:

- **Functional and physical safety (Machinery Regulation)**: Regulation (EU) 2023/1230 governs the risk of physical injury to people or damage to property. It requires that control-system failures or external interference not lead to dangerous physical movement of machinery or the failure of emergency safety interlocks.

- **Cybersecurity of the digital component (CRA)**: the CRA is responsible for the integrity, confidentiality, and availability of the software or hardware integrated into machinery.

If machinery contains a digital component or software module capable of direct or indirect data transmission, that component is assessed against the essential requirements of Annex I of the CRA. The CRA complements the Machinery Regulation by protecting against cyberattacks at the level of the machine's digital infrastructure — a necessary precondition for its overall functional safety. Procedurally, the manufacturer compiles a single technical documentation file and issues a single declaration of conformity.

**Medical Devices Regulation (MDR) (EU) 2017/745: grounds for full exclusion**

**Nature of interaction: Excludes.**

Under **Article 2(2), point (a)** of the CRA, the regulation **does not apply** to products with digital elements covered by Regulation (EU) 2017/745 on medical devices (MDR). An equivalent exclusion applies under Article 2(2), point (b) for Regulation (EU) 2017/746 on in vitro diagnostic medical devices (IVDR).

The legal and technical reasons for fully excluding medical devices from the CRA's scope include:

1. **Existence of comprehensive sector-specific regulation**: the MDR contains its own set of requirements for software as a medical device (SaMD), as well as for software components embedded in medical equipment. In particular, the General Safety and Performance Requirements (GSPR, Annex I to the MDR, points 14.2 and 17.2) require developers to ensure reliability, protection against unauthorised access, and a rigorous software development lifecycle.

2. **Priority of clinical risk assessment**: a cybersecurity breach in medical equipment directly affects patients' life and health. Dedicated guidance from the Medical Device Coordination Group (e.g. MDCG 2019-11, "Guidance on Cybersecurity for medical devices") sets a stricter regime for clinical testing and risk assessment than the CRA's horizontal standards.

3. **Avoiding procedural duplication**: bringing medical devices within the CRA's scope would create dual oversight from market surveillance authorities and notified bodies under the MDR. This would create regulatory delays in bringing critical medical products to market.

**Automotive regulation (UN R155, Regulation (EU) 2019/2144): a dedicated vehicle regime**

**Nature of interaction: Excludes.**

Under **Article 2(2), point (c)** of the CRA, products with digital elements governed by Regulation (EU) 2019/2144 of the European Parliament and of the Council on general vehicle safety requirements (General Safety Regulation II — GSR II) **are not covered** by this regulation.

The full exclusion of the automotive sector from the CRA reflects the existence of a specific international legal framework:

1. **Mandatory application of UN Regulations**: the automotive industry is regulated under Regulation (EU) 2019/2144 via UN Regulation No. 155 on a Cybersecurity Management System (CSMS) and UN Regulation No. 156 on a Software Update Management System (SUMS).

2. **End-to-end supply-chain coverage**: UN R155 requires vehicle manufacturers (OEMs) to demonstrate a certified CSMS extending to all component suppliers (Tier 1, Tier 2), including requirements for threat monitoring, vulnerability analysis, and incident response.

3. **A distinct type-approval procedure**: vehicles are subject to mandatory prior type-approval by national Type Approval Authorities, with the involvement of technical services, before series production begins. This model is fundamentally different from the market surveillance and self-declaration system used by the CRA.

**GDPR (EU) 2016/679: synergy between privacy and technical protection**

**Nature of interaction: Complements.**

The CRA neither excludes nor limits the application of the General Data Protection Regulation (GDPR). The two regulations reinforce each other: the GDPR sets the legal basis and principles for processing natural persons' personal data, while the CRA sets mandatory technical security criteria for the products used to carry out that processing.

The two acts interact along the following lines:

1. **Technical support for Article 32 GDPR (security of processing)**:

  - Article 32 of the GDPR requires controllers and processors to implement appropriate technical and organisational measures to secure data processing. The CRA provides regulatory assurance that devices and software placed on the market are designed under the "Security by Design and by Default" principle (Annex I, Part I of the CRA). This makes it easier for controllers to meet their obligation to choose secure processing tools.

2. **Institutionalising data-minimisation principles**:

  - Annex I, point 2(g) of the CRA expressly requires manufacturers to design products so that they process only the data (personal or otherwise) that is adequate, relevant, and limited to what is necessary for the device's functions. This requirement is the technical embodiment of Articles 5(1)(c) and 25 of the GDPR (data protection by design and by default).

3. **Cooperation between supervisory authorities**:

  - Article 54(7) of the CRA requires CRA market surveillance authorities to cooperate with the Data Protection Authorities (DPAs) established under the GDPR where vulnerabilities or incidents are found in products that risk breaching the confidentiality of personal data.

**Cybersecurity Act (CSA) (EU) 2019/881: presumption of conformity via the EUCC scheme**

**Nature of interaction: Overlaps and complements.**

Regulation (EU) 2019/881 (the Cybersecurity Act — CSA) established the European cybersecurity certification framework, tasking ENISA with developing unified certification schemes for ICT products, processes, and services. The CRA directly integrates this framework as a tool for demonstrating conformity.

The key certification scheme developed under the CSA that provides a presumption of conformity with CRA requirements is the **European Common Criteria Cybersecurity Certification Scheme (EUCC)**.

The legal mechanism linking the CSA and the CRA includes the following elements:

1. **Statutory recognition of the presumption of conformity**:

  - Under **Article 27(8) of the CRA**, products with digital elements for which an EU statement of conformity or a certificate has been issued under a cybersecurity certification scheme adopted pursuant to the CSA (including EUCC) are presumed to meet the essential cybersecurity requirements of Annex I to the CRA — to the extent that statement or certificate covers those requirements. Separately, under **Article 27(9)**, holding a European cybersecurity certificate at an assurance level of at least "substantial" removes the manufacturer's obligation to undergo third-party conformity assessment for the corresponding requirements (Article 32(2)(a)–(b) and 32(3)(a)–(b)).

2. **Simplified assessment for "important" and "critical" products**:

  - For standard products (roughly 90% of the market), manufacturers use the internal control procedure (Module A).

  - "Important" products, Class I and II (Annex III of the CRA), and "critical" products (Annex IV of the CRA), require mandatory third-party involvement (a notified body) or independent certification. Holding an EUCC certificate under the CSA allows a manufacturer to use it to cover these requirements without repeating testing.

3. **The Commission's power to adopt delegated acts**:

  - Article 8(1) of the CRA gives the European Commission the power to adopt delegated acts requiring manufacturers of specific categories of critical products to obtain certificates specifically under the CSA's EUCC scheme in order to be entitled to affix the CE marking and move freely within the EU internal market.
