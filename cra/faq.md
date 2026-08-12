**Practical FAQ for hardware and IoT manufacturers on the Cyber Resilience Act (Regulation (EU) 2024/2847)**

This section answers the most common practical questions raised by small and medium hardware manufacturers, IoT device developers, and digital-solution suppliers during the European Commission's public consultations, ENISA expert webinars, and professional discussions.

**1. I'm a small maker who sells craft IoT electronics on platforms like Etsy or my own website. Does the CRA apply to my products?**

**Answer:** Yes. The CRA sets no minimum threshold based on sales volume, revenue, or company size. Under Article 2(1), the CRA applies to all products with digital elements (PDEs) made available on the EU market in the course of a commercial activity. Selling devices through online platforms (Etsy, Shopify, Amazon) or your own website to consumers in the EU counts as commercially making a product available on the market.

However, significant simplifications apply for micro- and small enterprises:

- Roughly 90% of standard IoT products are assessed under **Module A** (self-assessment, no paid notified bodies involved).

- Under Article 64(10)(a), micro- and small enterprises are exempt from administrative fines for missing the initial procedural deadlines for vulnerability notification under Article 14(2)(a).

**2. I build and test prototypes, or ship small test batches for market research. Does the CRA apply to them?**

**Answer:** *For prototypes:* No. Prototypes, test samples, and products shown at exhibitions or still in development, that **have not yet been placed on the market for commercial use**, are excluded from the scope of the CRA (Article 2). *For small test batches:* if a test batch is given away or sold to end users for commercial use or ongoing operation in the EU, this is legally considered "making available on the market." In that case, the product must comply with the CRA.

**3. Our company is based outside the EU (e.g. in Asia or the US), but we sell hardware/IoT into Europe through distributors or marketplaces. Who is responsible for CRA compliance?**

**Answer:** Primary legal responsibility for development, code security, and conducting the conformity assessment rests with the **manufacturer**, regardless of its geographic location (Articles 13, 64).

At the same time, the CRA creates a chain of joint responsibility:

- **The EU importer** (under Article 19) must verify the presence of technical documentation, the declaration of conformity, and the CE marking before importing the product.

- If an importer or distributor sells the product under its own trademark (white-label) or makes a substantial modification to it, it legally acquires manufacturer status with the full obligations under Article 21 (this is the article governing cases where manufacturer obligations apply to importers and distributors; Article 22 covers other, broader cases of a third party acquiring manufacturer status).

**4. What happens to devices we placed on the EU market before December 2027? Do we need to withdraw or update products already sold?**

**Answer:** The CRA applies to products **placed on the market** after 11 December 2027 (Article 69). Products placed on the market before that date do not require re-certification or CE marking.

**Important exception:** the obligation to report discovered and actively exploited vulnerabilities under Article 14 applies to all products still in use and still supported by the manufacturer, starting from **11 September 2026**. In addition, if a device undergoes a "substantial modification" after December 2027, it will be treated as a new product and will require full CRA compliance.

**5. Our commercial IoT device uses open-source libraries and firmware (FOSS). Who is responsible for vulnerabilities in that open-source code?**

**Answer:** Responsibility rests entirely with the **manufacturer of the commercial product** (Recitals 15–18, Article 13). Non-profit open-source developers themselves are exempt from CRA obligations.

If you integrate FOSS into your commercial product, you must:

1. Carry out due diligence and verify the component has no known vulnerabilities.

2. Include the component in the software bill of materials (**SBOM**).

3. Release your own security updates if a flaw is found in the open-source library, throughout the product's entire support period.

**6. Who are "open-source software stewards" and what are their obligations?**

**Answer:** An *open-source software steward* is a legal entity (e.g. non-profit foundations like the Eclipse Foundation or the Linux Foundation) that provides infrastructure and systematically supports the development of open-source software intended for commercial use, without itself acting as the manufacturer of end products.

For such organisations, the CRA provides a lighter regime: they must implement a coordinated vulnerability disclosure policy and report discovered threats, but are not subject to certification requirements, full technical documentation obligations, or fines under Article 64.

**7. On average, how much time and money does a small or medium manufacturer (SME) need to bring a product into CRA compliance?**

**Answer:** Based on estimates from EU support-programme research (OCCTET, SECURE4SME) and market analysis data:

- **Time:** preparing a product of average complexity (implementing secure-coding processes, compiling technical documentation, building an SBOM) takes **6 to 12 months**.

- **Cost:** for a standard product under Module A (self-assessment), direct and indirect costs range from **EUR 10,000 to 30,000** per product. If the product is Class I/II or Critical and requires external assessment by a notified body, costs can reach **EUR 50,000–100,000+**.

**8. How is the support period for security updates determined for an IoT device, and is there a mandatory minimum term?**

**Answer:** Yes, there is — and this is a common misconception worth clearing up. Article 13(8) expressly states: **the support period must be at least 5 years**. The exception runs only one way: if the product's expected service life is shorter than 5 years, the support period may match that shorter term — but not the other way around. Five years is a legal minimum for any product with digital elements, not a rough regulatory expectation for "most consumer devices." A manufacturer that sets a shorter period without grounds of a "shorter expected use time" is in breach of Article 13(8). Support-period information must be clearly stated to the buyer before purchase.

**9. Does the CE marking need to be affixed to the plastic housing of a microcontroller or a small IoT board itself?**

**Answer:** Under Article 30(1)–(3), the CE marking is normally affixed directly to the product or its data plate.

However, where this is not possible due to the device's physical size, design, or nature (e.g. a microboard or sensor a few millimetres across), the CE marking may instead be affixed to the **packaging** and the **accompanying instructions/documentation**.

**10. We're developing an expansion board (shield/module) for Raspberry Pi or Arduino. Is that a spare part or a full product under the CRA?**

**Answer:** If the expansion board is a ready-to-use module with its own microcontroller or network interface (Wi-Fi, Bluetooth, Ethernet) and is sold to end users as a functional unit, it is considered a **product with digital elements (PDE)** and falls within the scope of the CRA.

The only exclusion under Article 2(6) is **spare parts** manufactured to the same specifications, for replacing identical components in already-released products.

**11. Is it true that most ordinary IoT devices (smart bulbs, simple sensors) don't need external assessment?**

**Answer:** Yes, that's correct. Roughly **90% of all products** with digital elements fall into the standard (non-critical) category.

For these, the conformity assessment procedure is based on internal manufacturing control — **Module A**. The manufacturer carries out the cybersecurity risk assessment itself, prepares the technical documentation, issues the EU declaration of conformity, and affixes the CE marking without involving any external labs or certification bodies.

**12. Which specific IoT products are considered "Important" or "Critical" and require mandatory third-party assessment?**

**Answer:** The specific categories are set out in Annexes III and IV of the CRA:

- **Important products, Class I:** routers, password managers, antivirus software, network management systems, and smart home products with security functionalities (smart locks, security cameras, alarm systems, baby monitors).

- **Important products, Class II:** hypervisors and container runtime environments, firewalls, intrusion detection and prevention systems (IDS/IPS), tamper-resistant microprocessors and microcontrollers.

- **Critical products (Annex IV):** hardware devices with security boxes (e.g. HSMs), electricity smart meter gateways, and smartcards and similar devices, including secure elements — this is the exhaustive three-item list from Annex IV, not a generalisation to all "critical infrastructure."

For Class II and Critical products, self-assessment is prohibited: a type examination (Modules B+C) or a quality assurance assessment (Module H) by a notified body is required.

**13. If a critical vulnerability is found in our IoT device, how much time do we have to notify EU authorities?**

**Answer:** Starting **11 September 2026** (Article 14), a strict three-stage notification timeline applies via ENISA's Single Reporting Platform:

1. **Early warning** — within **24 hours** of discovering active exploitation of a vulnerability or a severe incident.

2. **Vulnerability notification** — within **72 hours**, with general information about the threat.

3. **Final report** — within **14 days** of a remediation update (patch) being released.

**14. What is an SBOM (Software Bill of Materials), and are we required to publish it openly for buyers?**

**Answer:** An **SBOM** is a structured, machine-readable list of all software components, modules, libraries, and their versions that make up a device's software or firmware.

Under Annex I (Part II, point 1), the manufacturer must create and keep an up-to-date SBOM as part of its **internal technical documentation**. Publishing the SBOM openly for end consumers is **not required**. However, it must be ready to provide to market surveillance authorities on their official request.

**15. Can you avoid CRA responsibility by selling an IoT device as a DIY kit ("Do-It-Yourself" assembly kit)?**

**Answer:** (This question has not been officially clarified in a dedicated document — below is the most well-grounded legal interpretation based on EU harmonisation-legislation norms):

No, selling a device as an assembly kit does not let you bypass the CRA. If a DIY kit contains components with digital elements (e.g. a pre-programmed board, a microcontroller, or base software) and is intended to build a functional connected product, the supplier is considered the manufacturer of that product. The kit's manufacturer must ensure the security of the hardware modules and firmware it supplies, provide safe-assembly instructions, and update the code if vulnerabilities are found.

**16. Where can small and medium enterprises (SMEs) get financial or tooling support to adapt to the CRA?**

**Answer:** The European Commission, in Article 26, expressly provides for the creation of guidance materials and support tools for SMEs and startups.

Several dedicated EU-backed grant and technical initiatives are currently active:

- **The OCCTET project** (*Open-source Compliance: Comprehensive Techniques and Essential Tools*): provides free open-source tools for automated SBOM generation, dependency scanning, and preparation of CRA technical reports.

- **The SECURE4SME project**: runs open calls under which small and medium manufacturers can receive direct funding (micro-grants) for conformity assessment and cybersecurity testing.
