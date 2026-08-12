**Regulation (EU) 2024/2847 (Cyber Resilience Act): a comprehensive analysis of its regulatory scope, requirements, and institutional architecture**

**Background, regulatory context, and objective**

Regulation (EU) 2024/2847 of the European Parliament and of the Council of 23 October 2024 on horizontal cybersecurity requirements for products with digital elements, known as the Cyber Resilience Act (CRA), creates a single legal framework for ensuring the cybersecurity of digital products on the EU market.

The CRA's adoption is driven by the rapid digitalisation of industry and everyday life, where network-connected devices and software have become critical infrastructure for society. The growth in the number of connected devices has been accompanied by an escalation in cyber threats and large-scale cyber incidents. The European Commission estimates that the global annual cost of cybercrime has reached EUR 5.5 trillion.

The regulation is intended to address two fundamental market problems:

- A low baseline level of cybersecurity in many products with digital elements, reflected in widespread vulnerabilities, a lack of security-by-design foundations, and ineffective or inconsistent provision of security updates over the product lifecycle.

- Information asymmetry and a lack of transparency for end users, who are unable to objectively assess a product's level of security when choosing and using it.

The CRA is horizontal legislation. This means it sets unified, mandatory requirements across the full range of hardware and software products supplied to the EU market, regardless of their sector of use, except for a narrow list of specifically regulated sectors.

**Key dates, legal deadlines, and the application regime**

The CRA's adoption and rollout draws a clear distinction between the date of official publication, the date of entry into force, and the date of full application, and sets intermediate milestones for specific obligations.

Regulation (EU) 2024/2847 was officially published in the EU Official Journal on 20 November 2024. It entered into force on 10 December 2024 — the twentieth day after publication. From that date, the regulation officially became part of EU law, starting the legal countdown for the transitional periods. Full application of all the CRA's core requirements begins on 11 December 2027. From that date, no product with digital elements may be initially placed on the EU market without full compliance with the CRA's requirements.

| **Event/regulatory milestone** | **Legal date** | **Regulatory content and obligations** |
| --- | --- | --- |
| **Publication in the Official Journal** | 20 November 2024 | The final text of Regulation (EU) 2024/2847 is fixed. |
| **Entry into force** | 10 December 2024 | The legal countdown for the transitional periods begins. |
| **Designation of assessment bodies** | 11 June 2026 | Chapter IV takes effect. Member States must designate and notify conformity assessment bodies. |
| **Vulnerability reporting** | 11 September 2026 | Article 14 takes effect. Manufacturers must inform ENISA and CSIRTs of actively exploited vulnerabilities and severe incidents. |
| **Full application** | 11 December 2027 | Mandatory compliance with the essential cybersecurity requirements, technical documentation, and CE marking for all new products. |

Staggering the entry into force of individual provisions is meant to give conformity-assessment infrastructure and threat-monitoring processes time to be built up in advance.

**Subject matter of regulation, the PDE concept, and product categorisation**

The central object of CRA regulation is the "product with digital elements" (PDE). Under Article 3 of the regulation, a PDE is defined as any software or hardware product and its integrated remote data processing solutions, including individual software or hardware components being placed on the market, whose intended use, or reasonably foreseeable use, includes a direct or indirect logical or physical data connection to a device or network.

The scope covers two broad groups of products:

- Hardware with embedded software: any physical connected device, from consumer smart appliances to complex industrial equipment, sensors, programmable logic controllers, and network equipment.

- Standalone software: operating systems, PC and mobile apps, photo/video editing tools, password managers, antivirus software, firewalls, and remote administration tools.

The regulation also covers remote data processing solutions (RDPS), where such software is developed by the manufacturer (or on its behalf) and the absence of that cloud component would prevent the PDE from performing its core functions.

Depending on the level of cybersecurity risk and the potential consequences of compromise, the CRA divides all PDEs into four regulatory categories.

| **Product category** | **Product examples** | **Conformity assessment procedure** |
| --- | --- | --- |
| **Default products** (~90% of the market) | Text and photo editors, video games, smart toys, smart speakers, general-purpose mobile apps. | Manufacturer's internal control (self-declaration, Module A). |
| **Important products, Class I** (Annex III) | Password managers, network management systems, antivirus software, browsers, operating systems. | Application of harmonised standards (Module A) OR third-party assessment (Modules B+C or H). |
| **Important products, Class II** (Annex III) | Hypervisors and container runtime environments, firewalls, intrusion detection and prevention systems (IDS/IPS), tamper-resistant microprocessors and microcontrollers. | Mandatory notified-body involvement (Modules B+C or H). |
| **Critical products** (Annex IV) | Hardware security modules (hardware devices with security boxes), smart meter gateways, smartcards and similar devices, including secure elements. | Mandatory external certification or third-party assessment by a notified body. |

**Exclusions from scope and special legal regimes**

To avoid duplicating regulatory burden and creating regulatory conflicts, Article 2 of the CRA contains an exhaustive list of products and legal relationships that are fully or partially excluded from the regulation's scope.

Medical devices and in vitro diagnostic medical devices, regulated under Regulation (EU) 2017/745 (MDR) and Regulation (EU) 2017/746 (IVDR), are excluded from the CRA, since cybersecurity and risk-assessment requirements are already integrated into dedicated EU medical-device legislation. Airborne equipment, control systems, and civil aviation components covered by Regulation (EU) 2018/1139 are likewise not regulated under the CRA. Vehicles, automotive systems, and components subject to type-approval under Regulation (EU) 2019/2144 (which, in turn, requires compliance with UN Regulation No. 155, UN R155, on cybersecurity) are fully removed from the CRA's scope due to the existence of dedicated sector-specific rules. A similar exclusion applies to defence products developed or modified exclusively for defence or internal-security purposes, and to marine equipment regulated under Directive (EU) 2014/90/EU.

The regulation pays particular attention to cloud services and open-source software. Standalone Software-as-a-Service (SaaS) offerings that are not remote data processing solutions for a specific PDE are excluded from the CRA and are instead regulated under Directive (EU) 2022/2555 (NIS2). Free and open-source software (FOSS) developed or supplied outside the course of a commercial activity is also outside the CRA's scope. However, if an open-source component is integrated by a manufacturer into a commercial PDE, it is the manufacturer of the end product that bears full responsibility for its compliance with CRA requirements. For organisations that provide systematic support to open projects, a dedicated regulatory status of "open-source software stewards" has been introduced (Article 24), subject to a lighter compliance regime.

**Who must comply, and the extraterritorial "placing on the market" trigger**

The obligations set out in the CRA do not arise at the development or manufacturing stage as such — they are tied to the legal trigger of "placing on the EU market" or "making available on the EU market" in the course of a commercial activity.

The regulation has extraterritorial effect. The manufacturer's country of origin, jurisdiction of registration, or physical location is irrelevant. If a hardware or software product is available for purchase, download, or use by persons within the European Union in the course of commercial trade, the manufacturer must comply with the CRA.

The CRA clearly divides legal obligations among economic operators:

- Manufacturer: the natural or legal person that develops a PDE, or has one developed, and markets it under its own name or trademark. The manufacturer ensures development follows Security-by-Design principles, carries out the risk assessment, prepares the technical documentation, draws up the EU declaration of conformity, affixes the CE marking, and provides ongoing vulnerability support.

- Importer: an entity in the EU that places a product from a third country on the EU market. The importer must verify that the manufacturer has carried out the conformity assessment, that technical documentation and marking are in place, and must refuse to place a product on the market where there are grounds to consider it unsafe.

- Distributor: an entity in the supply chain that makes a product available on the market without altering its properties. The distributor must exercise due diligence to verify the CE marking and instructions are present before selling.

- Entities that substantially modify a product: if an importer, distributor, or other party makes a substantial modification to a PDE, it is treated as the manufacturer and takes on all CRA conformity assessment obligations.

**Structural anatomy of the regulation: chapters and annexes**

The legal text of Regulation (EU) 2024/2847 is highly detailed, consisting of 130 recitals, 8 chapters (containing 71 articles), and 8 annexes.

**Contents of the chapters**

Chapter I (General provisions, Articles 1–12) sets out the subject matter, scope, definitions (PDE, RDPS, vulnerability, substantial modification), the principles of free movement of products within the EU, and the interaction with the General Product Safety Regulation and the AI Act.

Chapter II (Obligations of economic operators and provisions on open-source software, Articles 13–26) contains a detailed list of manufacturers', importers', and distributors' obligations, the procedure for reporting vulnerabilities and incidents to ENISA (Article 14), the rules for establishing the Single Reporting Platform, and special rules for open-source software stewards (Article 24).

Chapter III (Conformity of the product with digital elements, Articles 27–34) governs the presumption of conformity, use of harmonised standards, CE-marking rules, conformity assessment procedures, and support measures for small and medium-sized businesses.

Chapter IV (Notification of conformity assessment bodies, Articles 35–51) sets requirements for notified bodies and the procedures for their accreditation, notification, and monitoring by national authorities.

Chapter V (Market surveillance and enforcement, Articles 52–60) sets out the powers of national market surveillance authorities, the procedures for withdrawing dangerous products from the market, and operational coordination mechanisms.

Chapter VI (Delegated powers and committee procedure, Articles 61–62) establishes the European Commission's powers to adopt delegated and implementing acts to adjust the lists of important and critical products.

Chapter VII (Confidentiality and penalties, Articles 63–65) sets out rules for protecting confidential information (Article 63), the procedure for applying administrative fines (Article 64), and rules on representative actions (Article 65).

Chapter VIII (Transitional and final provisions, Articles 66–71) contains transitional rules, sets out the timeline for individual articles entering into force, and amends related EU legal acts.

**Contents of the annexes**

Annex I (Essential cybersecurity requirements) is split into two parts: the first sets out the mandatory properties the product itself must have (protection against unauthorised access, confidentiality, integrity, minimising attack surfaces), and the second governs mandatory vulnerability-handling processes (a disclosure policy, providing free patches, building an SBOM).

Annex II (Information and instructions to the user) lists the mandatory information that must accompany every PDE, including the support period, secure setup, and a contact point for reporting vulnerabilities.

Annex III (Important products with digital elements) sets out the regulatory list of important products, split into Class I and Class II for the purposes of the conformity assessment procedure.

Annex IV (Critical products with digital elements) sets out the list of critical products that require the strictest third-party controls or external certification.

Annex V (EU declaration of conformity) sets the mandatory structure and content of the official declaration of conformity.

Annex VI (Simplified EU declaration of conformity) provides a simplified declaration template for certain categories of mass-market products.

Annex VII (Contents of the technical documentation) details the materials that must be included in a product's technical file, including the threat model, testing results, risk assessment, and SBOM.

Annex VIII (Conformity assessment procedures) describes the classic conformity assessment modules adapted for the CRA: Module A (internal control), Module B+C (EU type examination with type conformity), and Module H (full quality assurance).

**Interaction with CE marking and the EU regulatory system**

The CRA does not create a new or separate cybersecurity mark for products. Instead, the regulation extends the existing CE-marking system. Affixing the CE marking to a PDE indicates that the product complies with all applicable EU harmonisation directives and regulations, including the CRA's cyber-resilience requirements. A product with digital elements cannot lawfully be placed on the EU market without the CE marking.

Affixing the CE marking under the CRA requires completing a procedure that includes carrying out the cybersecurity risk assessment, meeting the essential requirements of Annex I, going through the appropriate conformity assessment procedure, and compiling the technical documentation and the EU declaration of conformity.

The CRA works in harmony with related EU regulatory acts:

- The NIS2 Directive (EU 2022/2555) governs the cybersecurity of critical entities and service operators, setting requirements for protecting their networks and systems. The CRA governs the cybersecurity of the digital products and components those entities use in their supply chains.

- The AI Act (Regulation (EU) 2024/1689) sets requirements for high-risk AI systems. If an AI system is a product with digital elements, it must meet the security requirements of both the AI Act and the CRA, with the CRA providing the unified cybersecurity assessment mechanisms.

- The Machinery Regulation (EU 2023/1230) and the Radio Equipment Directive (RED) are meant to be synchronised with the CRA in the future to eliminate dual oversight. That synchronisation has not yet happened for RED: RED's cybersecurity requirements (Article 3(3)(d)(e)(f), detailed in Delegated Regulation (EU) 2022/30) run in parallel with the CRA and have been legally binding since 1 August 2025 — that is, already today, well before the CRA's full application in December 2027 — for any connected equipment with a radio interface (Wi-Fi, Bluetooth, etc.).

**Institutional architecture of oversight, control, and regulatory support**

Compliance with the CRA is ensured through a two-tier institutional system spanning EU bodies and national structures in the Member States.

At EU level, the European Commission provides overall regulatory direction, adopts standardisation requests to CEN/CENELEC/ETSI, issues official guidance, and adopts delegated acts to adjust the product-category lists. The EU Agency for Cybersecurity (ENISA) plays the central operational role, building and administering the Single Reporting Platform (SRP). Manufacturers must submit notifications of actively exploited vulnerabilities and severe security incidents to this platform. ENISA also develops technical competence criteria for notified bodies and maintains the European vulnerability database.

At Member State level, each country designates national Market Surveillance Authorities (MSAs), which check compliance with CRA requirements on the domestic market. They are entitled to inspect products, demand technical documentation, forcibly withdraw dangerous products from the market, and impose sanctions. National Computer Security Incident Response Teams (CSIRTs) receive vulnerability notifications in parallel with ENISA via the SRP, to protect national infrastructure. Notifying authorities are responsible for accrediting, notifying, and monitoring private or public conformity assessment bodies (notified bodies).

| **Institutional body** | **Level of jurisdiction** | **Key functions and powers** |
| --- | --- | --- |
| **European Commission** | European Union | Rulemaking, standardisation requests, guidance, delegated acts. |
| **ENISA** | European Union | Administers the SRP, maintains the vulnerability database, sets technical criteria for CABs. |
| **Market surveillance authorities (MSAs)** | EU Member State | Inspecting products on the market, withdrawing dangerous goods, imposing fines. |
| **National CSIRTs** | EU Member State | Receiving vulnerability notifications and responding to incidents operationally. |
| **Notifying authorities** | EU Member State | Accrediting, notifying, and overseeing conformity assessment bodies. |

Penalties for CRA infringements are significant: non-compliance with the essential cybersecurity requirements carries fines of up to EUR 15 million or up to 2.5% of a company's global annual turnover for the preceding financial year, whichever is higher.

**Points of debate, legal ambiguity, and regulatory gaps**

Despite building a coherent regulatory framework overall, a number of the CRA's legal formulations and technical mechanisms carry regulatory ambiguity that poses a challenge for legal and technical practice.

**The boundary between SaaS and cloud-based remote data processing solutions (RDPS)**

Article 2 excludes pure SaaS from scope, while Article 3 and Annex I bring remote data processing solutions (RDPS) within CRA requirements. Where a physical device's or local app's functionality partly depends on a cloud API or microservices, the exact line between where an RDPS (covered by the CRA) ends and a standalone cloud service (covered by NIS2) begins remains blurred. Draft Commission guidance on the criteria for "how essential the absence of the cloud component is to the device's functioning" leaves room for subjective interpretation.

**Defining commercial activity for open-source software, and the limits of FOSS steward liability**

The CRA declares an exclusion for free, open-source software developed outside the course of a commercial activity. However, the wording of Recital 18 on what exactly constitutes "commercial activity" (e.g. accepting donations, offering paid consulting, having corporate development sponsors) creates legal uncertainty for non-profit foundations and developers. The special "Open-Source Software Steward" status (Article 24) imposes obligations on foundations to implement vulnerability-handling policies, but the scope of their legal liability if vulnerable code ends up in commercial products will need further precedent.

**Interpreting the support period and "expected service life"**

Under Article 13(8), the manufacturer must determine the product's support period — during which patches and vulnerability remediation are provided — based on the product's expected use time (taking into account user expectations, the nature of the product, and relevant EU law on product service life). The regulation sets a hard floor here: **the support period cannot be shorter than five years**, except where the product itself is expected to be used for less than five years — in which case the support period matches that shorter use time. A manufacturer that sets a support period shorter than five years for a product that is actually used for longer is in direct breach of CRA requirements.

**The harmonised-standards development timeline and time pressure**

To use the self-declaration procedure (Module A) for Important products, Class I, and to secure the presumption of conformity, manufacturers must rely on harmonised EU standards. The European Commission's standardisation request C(2025)618 to CEN/CENELEC covers a dozen complex specifications. The window between publication of the final standard texts and the CRA's full-application date (December 2027) is critically narrow. The absence of finalised standards forces manufacturers to carry out conformity assessment based on their own specifications, or to involve a notified body, increasing the financial burden.

**Duplication of incident-reporting obligations and friction between regulations**

Article 14 of the CRA requires reporting actively exploited vulnerabilities and severe incidents within 24 hours (early warning) and 72 hours (main notification) via the SRP to ENISA and CSIRTs. NIS2 and GDPR requirements apply in parallel. Manufacturers that are simultaneously NIS2 entities, or that process personal data, risk having to send several parallel notifications to different channels and regulators with different deadlines and formats.

**Conclusions and strategic recommendations for manufacturers**

Regulation (EU) 2024/2847 fundamentally changes the rules for developing, manufacturing, and distributing any product with digital elements on the EU market. Cybersecurity is shifting from an optional feature to a mandatory condition for market entry, on a par with electrical-safety or environmental requirements.

To ensure CRA compliance and minimise regulatory risk, manufacturers of hardware and software solutions need to carry out the following set of measures:

1. Product portfolio audit: classify every product and its components into the CRA categories (Default, Important Class I/II, Critical), checking for applicability of the Article 2 exclusions.

2. Comprehensive SBOM control: build automated tracking systems for all third-party and open-source libraries included in the product, to quickly identify and remediate vulnerabilities.

3. Reporting infrastructure: develop internal procedures for detecting, assessing, and reporting actively exploited vulnerabilities and incidents, to be ready to meet the 24/72-hour ENISA and CSIRT reporting deadlines from September 2026.

4. Security-by-Design and long-term support processes: integrate systematic cybersecurity risk assessment into the product design stages, and set and document a well-founded timeline for providing security updates to users.
