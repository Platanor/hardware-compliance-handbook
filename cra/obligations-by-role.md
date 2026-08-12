**Comparative analysis of economic operators' obligations under the Cyber Resilience Act: Manufacturer, Importer, Distributor**

**Legal framework and article numbering in Chapter II**

Chapter II of Regulation (EU) 2024/2847 of the European Parliament and of the Council of 23 October 2024 on horizontal cybersecurity requirements for products with digital elements (Cyber Resilience Act, CRA) sets out a clear division of legal and technical obligations among economic operators across the entire supply chain.

When analysing the text of the regulation published in the EU Official Journal on 20 November 2024, it's important to pay attention to precise article numbering, since early drafts and secondary analysis sometimes disagreed:

- **Article 13**: Obligations of manufacturers.

- **Article 14**: Reporting obligations of manufacturers (vulnerabilities and incidents).

- **Article 19**: Obligations of importers. *Note: in some earlier drafts this article appeared as Article 17, but in the final text of Regulation 2024/2847, importer obligations are set out in Article 19, while Article 17 covers other reporting provisions.*

- **Article 20**: Obligations of distributors. *Note: in the final text, distributor obligations are set out in Article 20 (not Article 19).*

- **Article 21**: Cases in which obligations of manufacturers apply to importers and distributors.

- **Article 22**: Other cases in which manufacturer obligations apply.

Economic operators' obligations apply according to the general phased timeline: the core product-compliance requirements become mandatory from 11 December 2027, while the Article 14 reporting requirements take effect earlier — from 11 September 2026.

**Manufacturer obligations — Articles 13 and 14**

The manufacturer bears the primary and most comprehensive responsibility for the cybersecurity of a product with digital elements (PDE) throughout its design, development, production, and subsequent lifecycle.

**Full list of manufacturer obligations (Article 13)**

1. **Design under the Security-by-Design and Security-by-Default principles (Article 13(1))**: the manufacturer must ensure the PDE is designed, developed, and produced in accordance with the essential cybersecurity requirements set out in Part I of Annex I. The product must ship with a secure default configuration and a minimised attack surface. **Important nuance**: only point 1 of Part I of Annex I is unconditional. Each of the following thirteen specific sub-points (2(a)–2(m): absence of known exploitable vulnerabilities, secure by default, encryption, etc.) is expressly qualified by "on the basis of the cybersecurity risk assessment ... and where applicable" — i.e. this is not a single unconditional checklist for every product, but a list whose applicability is determined by the manufacturer's own risk assessment.

2. **Cybersecurity risk assessment (Article 13(2)–(4))**: the manufacturer must carry out and document a cybersecurity risk assessment, taking into account the product's intended and reasonably foreseeable use. The risk assessment is incorporated into the technical documentation (Annex VII) and updated throughout the support period.

3. **Due diligence on third-party components (SBOM, Article 13(5))**: when integrating third-party components (including free and open-source software, FOSS), the manufacturer must exercise due diligence to ensure such components do not compromise the PDE's security. The manufacturer must create and maintain a software bill of materials (SBOM) covering at least the product's top-level dependencies.

4. **Vulnerability handling processes (Article 13(8), Annex I Part II)**: the manufacturer must identify and remediate vulnerabilities, carry out regular security testing, and maintain a public vulnerability disclosure policy and a contact point for security researchers. (Separately, Article 13(6) covers a narrower case — the obligation to report a discovered vulnerability to the developer of a third-party/open-source component if that is where the vulnerability resides.)

5. **Providing support throughout the support period (Article 13(8))**: the manufacturer must determine the product's support period, during which free security updates are released. This period must correspond to the product's expected service life.

6. **Conformity assessment and technical documentation (Article 13(3), Article 32, Annex VII)**: carrying out the applicable conformity assessment procedure (self-declaration under Module A, or notified-body involvement under Modules B+C / H) and compiling the technical file.

7. **Drawing up the EU declaration of conformity and CE marking (Article 13(12), Articles 28–30)**: the manufacturer draws up the official EU declaration of conformity per the template in Annex V or VI and affixes the CE mark to the product, its packaging, or accompanying documentation.

8. **User information and instructions (Article 13(18), Annex II)**: providing clear, understandable instructions for secure setup, use, and updating, and stating the end date of the support period.

**Vulnerability and incident reporting (Article 14)**

The manufacturer must notify ENISA (via the Single Reporting Platform) and the responsible national CSIRT of:

- **Actively exploited vulnerabilities**: an early warning within **24 hours** of discovery, a detailed notification within **72 hours**, and a final report within **14 days** of a patch being released.

- **Severe security incidents**: an early warning within **24 hours**, a detailed notification within **72 hours**, and a final report within **1 month**.

**Importer obligations — Article 19**

An importer is a natural or legal person established in the EU that places a product with digital elements originating from a third country (outside the EU) on the EU market. The importer acts as a regulatory filter before a foreign product is allowed onto the Union market.

**Key importer obligations (Article 19):**

1. **Only admitting compliant products (Article 19(1))**: the importer may only place on the EU market PDEs that meet the essential cybersecurity requirements of Part I of Annex I, and for which the manufacturer applies the vulnerability-handling processes set out in Part II of Annex I.

2. **Verification duties (Article 19(2))**: before placing a product on the market, the importer must verify that:

  - the manufacturer has carried out the appropriate conformity assessment procedure;

  - the manufacturer has prepared the technical documentation (Annex VII);

  - the product bears the CE marking;

  - the product is accompanied by the EU declaration of conformity and by user instructions and information (Annex II) in a language understood by consumers in the relevant Member State.

3. **Duty to withhold from the market and to inform (Article 19(3)–(4))**: if the importer believes, or has reason to believe, that a PDE does not comply with CRA requirements, it **may not** place the product on the market until it has been brought into compliance. If the product poses a cybersecurity risk, the importer must immediately inform the manufacturer and the market surveillance authorities (MSAs). If a vulnerability is found, the importer must inform the manufacturer.

4. **Importer identification on the product (Article 19(5))**: the importer must state its name, registered trade name or trademark, and postal and email address directly on the product, or, if that is not possible, on the packaging or in an accompanying document.

5. **Storage and transport conditions (Article 19(6))**: the importer must ensure that storage or transport conditions under its responsibility do not jeopardise the product's compliance with the essential cybersecurity requirements.

6. **Document retention (Article 19(7))**: the importer must keep a copy of the EU declaration of conformity and provide the technical documentation to market surveillance authorities on request, for **10 years** after the product is placed on the market or for the support period, whichever is longer.

7. **Cooperation with market surveillance authorities (Article 19(8))**: on a reasoned request from an MSA, provide all information and documentation needed to demonstrate the product's compliance.

**Distributor obligations — Article 20**

A distributor is any person in the EU supply chain, other than the manufacturer or importer, who makes a product available on the market without altering its properties (e.g. retailers, wholesalers, marketplaces). The distributor has the lightest set of obligations and acts on a "due care" principle.

**List of distributor obligations (Article 20):**

1. **Due-care principle (Article 20(1))**: when making a PDE available on the market, the distributor must act with due care regarding compliance with CRA requirements.

2. **Pre-sale checks (Article 20(2))**: before making a product available on the market, the distributor must verify the formal indicators of compliance are present:

  - the **CE** marking on the product or its packaging;

  - that the manufacturer and importer have fulfilled their obligations to provide instructions and accompanying documents in the language of the relevant Member State (Annex II);

  - that the manufacturer's and importer's details (name, address) are present.

3. **Prohibition on selling non-compliant goods (Article 20(3))**: if the distributor believes, or has reason to believe, that a product does not meet the CRA's essential requirements, it must not make it available on the market until it has been brought into compliance. Where there is a cybersecurity risk, it must inform the manufacturer/importer and the MSAs.

4. **Storage and transport conditions (Article 20(4))**: ensuring appropriate storage and logistics conditions that do not degrade the product's security status.

5. **Taking corrective action (Article 20(5))**: where non-compliance is found in a product already made available on the market, ensuring corrective action is taken by the manufacturer or importer (withdrawal from the market, recall, patch release).

6. **Cooperation with surveillance authorities (Article 20(6))**: providing MSAs with information and documentation confirming compliance.

**Reclassification of economic operators — Article 21**

Article 21 of Regulation (EU) 2024/2847 sets out the legal conditions under which an importer or distributor loses its lighter-obligation status and **is treated as a manufacturer** (taking on the full scope of obligations under Articles 13 and 14):

1. **Rebranding (selling under one's own trademark)**: where an importer or distributor places a PDE on the market under its own name or trademark.

2. **Substantial modification**: where an importer or distributor makes a substantial modification to a PDE already placed on the market that affects its compliance with the cybersecurity requirements or changes its intended purpose.

**Combined obligations comparison matrix**

The table below summarises the obligations of each of the three economic operators.

| **Obligation/procedure under the CRA** | **Manufacturer, Art. 13-14** | **Importer, Art. 19** | **Distributor, Art. 20** |
| --- | --- | --- | --- |
| **Security-by-Design & Default** | **Direct obligation**: design and development (Annex I) | Verifies the manufacturer has done this | Not directly applicable |
| **Cybersecurity risk assessment** | **Direct obligation**: carrying out and documenting it | Verifies presence in the technical file | No requirement to check the risk file |
| **Building the SBOM and FOSS due diligence** | **Direct obligation**: maintaining the SBOM and auditing components | Does not check the SBOM directly | Not applicable |
| **Vulnerability handling and patching** | **Direct obligation**: releasing patches throughout the support period | Informs the manufacturer of found vulnerabilities | Informs the manufacturer/importer |
| **Reporting vulnerabilities to ENISA/CSIRTs (Art. 14)** | **Direct obligation**: 24h / 72h / 14d notifications | None (unless reclassified under Art. 21) | None |
| **Carrying out conformity assessment** | **Direct obligation**: Module A, B+C, or H | Verifies the procedure was carried out | Does not check the procedure |
| **Drawing up technical documentation** | **Direct obligation**: compiling the file (Annex VII) | Keeps a copy/ensures 10-year availability for MSAs | Does not retain technical documentation |
| **Drawing up the EU declaration of conformity** | **Direct obligation**: issues and signs it | Verifies the declaration exists | Verifies it accompanies the product |
| **Affixing CE marking** | **Direct obligation**: affixes the CE mark | Verifies the CE mark is present | Verifies the CE mark is present |
| **Affixing own identification details** | Name, trademark, address on the product | Name, trademark, address alongside the manufacturer's details | Verifies the manufacturer's and importer's details are present |
| **User instructions (Annex II)** | Creates and includes with the product | Verifies presence and language of instructions | Verifies presence in the required language |
| **Control of storage and transport conditions** | Ensures this at its own production/warehouses | **Direct obligation** during logistics | **Direct obligation** during storage/sale |
| **Cooperation with market surveillance authorities (MSAs)** | Provides information, fixes non-compliance | Provides documents, facilitates product withdrawal | Facilitates corrective action |

**A special case study: combined Importer/Manufacturer roles (OEM/ODM in Asia)**

**Scenario description**

"EU Brand Ltd", established and registered in an EU Member State, writes the technical specification and commissions an Asian OEM/ODM contract manufacturer (for example in Taiwan or China) to produce smart routers. The product is physically manufactured in Asia, branded with the "EU Brand Ltd" logo, and physically brought into (imported into) the EU by "EU Brand Ltd" for further distribution.

**Legal status under the CRA**

Under **Article 3, point 13** and **Article 21** of Regulation (EU) 2024/2847, when an economic operator commissions the design or manufacture of a product with digital elements and places it on the market under **its own name or trademark**, it qualifies as the **MANUFACTURER**.

In this scenario, "EU Brand Ltd" is **not treated as an ordinary importer**, despite physically handling customs clearance and the import of the goods from Asia. Article 21 automatically transfers the full scope of the manufacturer's legal and technical obligations under Articles 13 and 14 to the company.

**Practical consequences and division of obligations for the EU-based company:**

1. **No delegation of legal liability**: "EU Brand Ltd" cannot shift legal liability for CRA non-compliance onto its Asian OEM supplier. EU law treats "EU Brand Ltd" as the sole entity responsible for certification and security.

2. **Duty to oversee development (Security-by-Design)**: the company must contractually require the Asian contractor to follow the essential requirements of Annex I, carry out code audits, and provide a full SBOM and documentation confirming the absence of known vulnerabilities.

3. **Mandatory risk assessment and technical file**: "EU Brand Ltd" must, alone or together with the contractor, create and maintain technical documentation in accordance with Annex VII, including the cybersecurity risk assessment file.

4. **Reporting under Article 14**: if an actively exploited vulnerability is discovered in the router, it is "EU Brand Ltd" that must send notifications to ENISA and the national CSIRT within 24/72 hours.

5. **Guaranteeing the support period**: the company must ensure security patches are released and distributed throughout the entire declared support period, even if the manufacturing contract with the Asian factory is terminated.

6. **Declaration and marking**: "EU Brand Ltd" signs the EU declaration of conformity in its own name and affixes the CE marking.

**Conclusions**

Regulation (EU) 2024/2847 creates a strict and transparent hierarchy of accountability. While manufacturers bear the full cycle of responsibility for a product's engineering security and operational support (Articles 13, 14), importers (Article 19) and distributors (Article 20) perform the critical function of verifying formal compliance. At the same time, Article 21 warns any EU company against attempting a "simple import" of goods under its own brand without accepting the full obligations of a manufacturer.
