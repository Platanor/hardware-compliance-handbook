**Legal and technical analysis of the EU Cyber Resilience Act (EU 2024/2847): official definitions, terminology, and regulatory nuances**

**Implementation framework and the significance of the terminology in Regulation (EU) 2024/2847**

Regulation (EU) 2024/2847 of the European Parliament and of the Council on horizontal cybersecurity requirements for products with digital elements, known as the Cyber Resilience Act (CRA), was officially published in the EU Official Journal on 20 November 2024 and entered into force on 10 December 2024. This legal act introduces a unified legal framework of mandatory cybersecurity requirements for hardware and software throughout the entire lifecycle of the relevant products.

The CRA's provisions take effect according to a clear phased implementation schedule:

- From 10 December 2024, the regulation is in force as an EU legal act.

- From 11 June 2026, the Chapter IV provisions on notifying conformity assessment bodies start to apply.

- From 11 September 2026, the Article 14 requirements on notifying actively exploited vulnerabilities and security incidents become mandatory.

- From 11 December 2027, the regulation is fully applicable, including mandatory CE marking and conformity assessment procedures.

Within the EU legal system, the definitions set out in Article 3 of Regulation (EU) 2024/2847 function not merely as a glossary of terms, but as the qualifying basis for determining the legal scope of economic operators' liability and the boundaries within which enforcement mechanisms apply.

**Detailed legal and technical analysis of Article 3 definitions and related provisions**

**Product with digital elements (PDE)**

The official definition is set out in Article 3, point 1 of Regulation (EU) 2024/2847. It means any software or hardware product and its remote data processing solutions, including software or hardware components being placed on the market separately.

In plain terms, this covers any digital or physical device or software intended for direct or indirect connection to a network or to other devices. This includes both physical goods (operating systems, smartwatches, routers, industrial PLCs) and standalone software (mobile apps, desktop programs, individual code libraries).

Practical ambiguity arises in distinguishing a PDE from a standalone cloud service (SaaS). Purely cloud-based services are regulated under NIS2 and are not products within the meaning of the CRA. However, if a remote cloud backend is developed by the device's manufacturer and is necessary for at least one of the product's core functions, that backend is treated as a remote data processing solution and is included within the PDE. A further discussion concerns custom software: the European Commission's clarifications state that software built to a specific order for a single client, without being placed on the market publicly, is treated as a service and falls outside the CRA, but replicated web modules or plugins qualify as PDEs.

**Manufacturer**

The official definition is given in Article 3, point 14 of the regulation. This is any natural or legal person that develops or manufactures a product with digital elements, or has one developed or manufactured, and markets it under its own name or trademark.

In plain terms, the manufacturer is the company or developer that creates software or hardware and markets it under its own brand.

The main practical ambiguity lies in distinguishing between the original developer and an OEM repackager (white-label). If a company buys a finished digital product from a third party, or integrates open-source code, and then sells it under its own brand, it takes on the legal status of "manufacturer" with the full scope of obligations. These obligations include compiling technical documentation, releasing patches, maintaining an SBOM (Software Bill of Materials), and handling vulnerabilities throughout the entire support period.

**Importer**

The official definition is set out in Article 3, point 16 of the regulation. An importer is any natural or legal person established in the European Union that places on the Union market a product with digital elements bearing the name or trademark of a person established in a third country.

In plain terms, this is an EU-resident company that brings in a digital device or software from a foreign developer (e.g. from the US, UK, or Ukraine) and is the first to sell it on the EU market.

A practical dispute arises around digital distribution over the internet. When a foreign developer supplies software directly to an end consumer in the EU through its own website, with no EU legal entity involved, there is no physical importer. In that case, the foreign developer acts directly as the manufacturer, but an authorised representative established in the Union is required for oversight by EU market surveillance authorities.

**Distributor**

The official definition is contained in Article 3, point 17 of the regulation. This is any natural or legal person in the supply chain, other than the manufacturer or the importer, that makes a product with digital elements available on the market without affecting its properties.

In plain terms, this is a reseller, retail shop, or digital sales platform that resells a finished product already made by the manufacturer or brought in by the importer.

The practical ambiguity relates to how far a distributor may go in modifying the product's configuration. If, before selling, a distributor installs its own software on the device, changes the factory security configuration, or repackages the software, it stops being a distributor and is treated as having carried out a "substantial modification," automatically acquiring manufacturer status.

**Economic operator**

The official definition is set out in Article 3, point 18 of the regulation. The term covers the manufacturer, the authorised representative, the importer, the distributor, a free and open-source software steward, or any other natural or legal person subject to obligations in relation to the manufacture of products with digital elements or making them available on the market.

In plain terms, this is an umbrella regulatory term for any legal or natural person involved in the business chain of manufacturing, supplying, supporting, or selling digital products in the EU.

The key regulatory nuance is that the scope of an economic operator's legal liability depends on its specific role. Including "free and open-source software stewards" among economic operators was the subject of lengthy discussion during the EU's trilogue negotiations, since it required creating a special, lighter regulatory regime for them compared to conventional commercial manufacturers.

**Substantial modification**

The official definition is given in Article 3, point 23 of the regulation. This is a change to a product with digital elements, made after it has been placed on the market, that affects the product's compliance with the essential cybersecurity requirements or changes the intended purpose for which the product was assessed.

In plain terms, this is any deep modification to hardware or software that changes its functions, security architecture, or level of cybersecurity risk.

This is one of the CRA's most contested legal and technical points. Standard security updates that fix discovered vulnerabilities without changing functionality are explicitly defined by the regulation as NOT constituting a substantial modification. However, adding new network protocols, integrating new AI modules, or fundamentally changing the access-control system is considered a substantial modification. The person carrying out such a modification legally becomes the "manufacturer" of the modified product and must carry out a new conformity assessment and update the CE marking.

**Remote data processing solution**

The official definition is set out in Article 3, point 3 of the regulation. This is remote data processing for which the software is designed and developed by, or on behalf of, the manufacturer of the product with digital elements in question, and the absence of which would prevent the product from performing one of its functions.

In plain terms, this is a cloud server or backend controlled by the device's manufacturer, without which the device or mobile app cannot function properly.

Discussion arises around the highlighted criterion "the absence of which would prevent it from performing one of its functions." If a device (e.g. a smart thermostat) can be adjusted manually on its own panel without a server connection, but its remote mobile control requires the developer's cloud, the Commission treats that cloud as a remote data processing solution. Consequently, the developer's entire cloud infrastructure must be audited for compliance with the CRA's cybersecurity requirements alongside the thermostat itself.

**Vulnerability**

The official definition is contained in Article 3, point 8 of the regulation. A vulnerability means a weakness, susceptibility, or flaw in a product with digital elements that can be exploited by a cyber threat.

In plain terms, this is a bug in the code or a flaw in the device's design that lets hackers break into the system, steal data, or disrupt its operation.

The practical boundary lies between an ordinary functional software bug and a security bug. If a bug only causes a button in an app to change colour, it is not a vulnerability. A bug becomes a vulnerability under the CRA only where it has the technical potential to compromise the confidentiality, integrity, or availability of the system or its data.

**Actively exploited vulnerability**

The official definition is given in Article 3, point 9 of the regulation. This is a vulnerability for which there is reliable evidence that a malicious actor has executed malicious code on a system without the authorisation of the system's owner.

In plain terms, this is a security "hole" that is known for certain to be exploited by hackers right now, in real attacks.

The main ambiguity concerns the term "reliable evidence" and the Article 14 reporting clock. A lab-based proof-of-concept demonstration is not active exploitation. However, even a single confirmed instance of real unauthorised modification or code execution triggers the manufacturer's obligation to submit an early warning to ENISA and the responsible CSIRT within 24 hours.

**Security update**

The official definition is given in Article 3, point 26 of the regulation. This is a software update, including a patch, that addresses identified cybersecurity vulnerabilities.

In plain terms, this is a technical fix (patch) that closes a discovered vulnerability.

The regulation requires a strict legal separation of security patches from feature updates. Manufacturers are prohibited from bundling mandatory security fixes with the addition of new paid functionality or a change to the user agreement. Security patches must be provided free of charge and installable with as little friction as possible.

**Support period**

The official definition is set out in Article 3, point 27 of the regulation. This is the period during which a manufacturer ensures the effective handling of vulnerabilities in a product with digital elements, in accordance with the requirements of the regulation.

In plain terms, this is the product's expected service life, during which the developer must release patches and monitor security.

The regulation sets a legal minimum here: under Article 13(8), the support period must be **at least 5 years**, except where the product's expected use time is shorter — in which case the support period matches that shorter term. The manufacturer determines the specific duration (beyond this minimum) itself, based on the product's expected use time, and regulators are entitled to challenge an unreasonably short period set in breach of this rule (for example, if an industrial router is only offered 1 year of support). Support-period information must be given to the buyer before the purchase agreement is concluded.

**Conformity assessment**

The official definition is set out in Article 3, point 30 of the regulation. This is the process of demonstrating that the essential cybersecurity requirements set out in Annex I have been met in relation to a product with digital elements.

In plain terms, this is a formal check (an internal audit, or an external review by an independent body) confirming that the product is secure as required by law.

The main contested point is the choice of procedural module (Module A, Module B+C, Module H). Manufacturers try to use self-assessment (Module A), but for important and critical products, notified body involvement is mandatory, creating technological and financial barriers.

**Essential cybersecurity requirements**

Officially established in Article 6 and detailed in Annex I (Parts I and II) of the regulation. These cover core principles: protection against unauthorised access, minimising attack surfaces, encryption, measures to limit the consequences of incidents, and systematic vulnerability management.

In plain terms, these are the security-architecture standards for development (Security by Design and Security by Default).

The practically difficult rule is the mandatory cybersecurity risk assessment. If any of the Annex I requirements is deemed not applicable to a specific product, the manufacturer must provide a legally and technically sound justification for that exception in the technical documentation (Annex VII).

**Free and open-source software steward**

The official definition is contained in Article 3, point 21 of the regulation. This is a legal person, other than a manufacturer, whose purpose or objective is to systematically provide sustained support for the development of free and open-source software intended for commercial activities.

In plain terms, these are non-profit foundations and organisations (e.g. the Linux Foundation, the Eclipse Foundation, the Apache Software Foundation) that maintain the infrastructure of open-source projects.

Discussion focused on the risk of imposing disproportionate financial and procedural burdens on open source. The CRA takes stewards out of the standard manufacturer requirements: they do not affix the CE marking and are not responsible for certification, but they must set up a vulnerability disclosure process.

**Open-source software made available on the market in the course of a commercial activity**

The official provisions are set out in Article 2, point 1, Recital 18, and the European Commission's clarifications. The regulation only covers open-source software that is made available on the market in the course of a commercial activity.

In plain terms, if code is created as a hobby and shared for free with no profit motive, the law does not apply to it. But if open code is part of a business model, it becomes subject to CRA requirements.

The criteria for the line between a hobby project and a commercial activity, per Recital 18 and the draft European Commission guidance:

- **Non-commercial activity (outside the CRA)**: a hobbyist developer writes code and accepts donations (e.g. via GitHub Sponsors) to cover running costs like server bills or coffee. Recital 18 expressly clarifies that merely receiving financial support from manufacturer companies, or their involvement in development, does not on its own turn a project into a commercial activity.

- **Commercial activity (falls under the CRA)**: the developer sells paid technical support or consulting services for the code (where the fee covers more than the actual cost of providing that support — Recital 15), uses dual licensing (a paid commercial licence alongside an extended AGPL), or integrates the code into a paid cloud service.

**Critical product / Important product (Class I / Class II)**

The official definitions are set out in Articles 7 and 8, and detailed in Annexes III and IV, as well as in Implementing Regulation (EU) 2025/2392 (the technical description of the categories, which Article 7(4) tasks the Commission with adopting).

- **Important product, Class I**: products performing protective functions (password managers, antivirus software, VPNs, web browsers, operating systems, routers/modems/switches, PKI infrastructure).

- **Important product, Class II**: higher-risk products (hypervisors and container runtime environments, firewalls, intrusion detection and prevention systems (IDS/IPS), tamper-resistant microprocessors and microcontrollers).

- **Critical product (Annex IV)**: products of critical dependency (smartcards, secure elements, smart meter gateways).

In plain terms, this is a grading of products by how dangerous their compromise would be for society and the economy. The higher the risk class, the stricter the assessment procedure.

A practical ambiguity was clarified by Implementing Regulation (EU) 2025/2392 of 28 November 2025: integrating a component that is itself an important product (e.g. a browser engine) into an ordinary application (e.g. a news app) does NOT turn the entire news app into an important product, Class I. Only a product whose *core functionality* matches the criteria in Annex III or IV is assessed under the higher class.

**CE marking in the context of the CRA**

The official definition is set out in Article 3, point 34, with the rules for applying it in Articles 29 and 30. This is a marking by which the manufacturer indicates that the product is in conformity with the applicable requirements set out in Union harmonisation legislation.

In plain terms, this is the "CE" mark confirming that the software or device has passed all the required cybersecurity checks.

Ambiguity arises when affixing the CE mark to standalone software (pure software) that has no physical packaging. The regulation allows the CE marking to be affixed virtually: in the "About" screen, in accompanying digital documentation, or in a declaration of conformity published on a website. From 11 December 2027, placing any PDE on the EU market without the CE marking will be prohibited.

**Summary of product categories and conformity assessment procedures**

Below is a comparative overview of the legal categories of products with digital elements and the applicable conformity assessment procedures.

| **CRA product category** | **Legal basis** | **Examples of digital products** | **Applicable conformity assessment module** |
| --- | --- | --- | --- |
| **Default products** | Article 6, general requirements | Text editors, video games, photo editors, general mobile apps | **Manufacturer self-assessment (Module A — internal control)** |
| **Important products, Class I** | Article 7, Annex III (Class I) | Password managers, web browsers, network interfaces, PKI infrastructure, routers/modems | Harmonised standards (Module A) **or** notified body involvement (Module B+C / H) |
| **Important products, Class II** | Article 7, Annex III (Class II) | Hypervisors, container runtime environments, firewalls, IDS/IPS | Mandatory third-party involvement: notified body (Module B+C / H) or an EU certificate |
| **Critical products** | Article 8, Annex IV | Hardware secure elements, smartcards, meter gateways | Mandatory European cybersecurity certification (Regulation (EU) 2019/881) |

**Conclusions and regulatory imperatives**

Regulation (EU) 2024/2847 fully transforms the architecture of legal liability in digital technology. It covers both traditional hardware solutions and non-commercial and commercial software alike, introducing fundamentally new requirements for vulnerability management and supply-chain transparency.

Timely adaptation of internal development processes, correctly establishing economic operators' status, and a legally sound classification of update types will let developers and suppliers minimise regulatory risk ahead of the CRA's mandatory compliance deadlines.
