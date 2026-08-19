**Product risk classification under the Cyber Resilience Act (Default, Important Class I/II, Critical)**

Regulation (EU) 2024/2847 of the European Parliament and of the Council (Cyber Resilience Act, CRA) introduces a risk-based regulatory system for products with digital elements (PDE). Instead of a single uniform procedural approach, the CRA divides all products into four regulatory categories (three risk tiers), which directly determine how strict the conformity assessment procedure is and how much involvement is required from external independent bodies (notified bodies).

Detailed technical descriptions of the important- and critical-product categories are set out in Commission Implementing Regulation (EU) 2025/2392 (entered into force 21 December 2025). **Caveat:** the full text of this implementing act is not part of our internal primary-source archive, so the specific detailed points below that reference 2025/2392 should be verified directly on EUR-Lex before being relied on for consequential decisions — the base categories and examples from Annex III/IV of Regulation (EU) 2024/2847 itself have been checked directly and are reliable.

**1. The general logic of the three-tier risk classification**

The CRA's regulatory philosophy is based on assessing the potential adverse consequences that a breach, malfunction, or vulnerability in a product could have for users, networks, and critical infrastructure.

```
+--------------------------------------------------------------------+
| CRITICAL PRODUCTS (Annex IV)                                       |
| Mandatory European certification or notified body                 |
+--------------------------------------------------------------------+
| IMPORTANT PRODUCTS, CLASS II (Annex III)                           |
| Mandatory notified body involvement                                |
+--------------------------------------------------------------------+
| IMPORTANT PRODUCTS, CLASS I (Annex III)                            |
| Self-assessment against standards OR notified body involvement     |
+--------------------------------------------------------------------+
| DEFAULT PRODUCTS                                                   |
| Manufacturer self-assessment (Module A)                            |
+--------------------------------------------------------------------+
```

1. **Default products (standard category)**: cover the vast majority of digital products on the market (per third-party estimates, roughly 90% of software and hardware; the regulation itself does not state this percentage). They perform no critical security functions and have no systemic impact on overall network security.

2. **Important products (Annex III)**: split into **Class I** and **Class II** depending on their cybersecurity risk level and their role in maintaining system integrity or processing sensitive data.

3. **Critical products (Annex IV)**: products with the highest cybersecurity risk, whose compromise creates a threat of systemic disruption in critical economic sectors or to state security.

**2. Full list of Annex III Class I categories (Important products, Class I)**

Class I products fall into this category because they perform protective functions, manage access, handle credentials, or are network nodes or widely used platforms whose compromise enables large-scale attack vectors.

Under Annex III of Regulation (EU) 2024/2847 and Implementing Regulation (EU) 2025/2392, **Class I** consists of the following 19 product categories:

1. **Identity management and privileged access management (PAM) software**: software for authentication, account management, and access control, including authentication and access-control devices — including biometric readers.

2. **Standalone and embedded browsers**: web browsers that are the primary interface for interacting with the internet.

3. **Password managers**: applications for storing, generating, and encrypting credentials.

4. **Software that searches for, removes, or quarantines malicious software (antivirus/anti-malware)**: antivirus tools and threat scanners.

5. **Products with a virtual private network (VPN) function**: hardware and software VPN clients and gateways.

6. **Network management systems**: tools for administering, monitoring, and configuring network infrastructure.

7. **Security Information and Event Management (SIEM) systems**: software for collecting, analysing, and correlating security events.

8. **Boot managers**: components that control the operating-system boot process and bootloader signature verification.

9. **Public key infrastructure (PKI) and digital certificate issuance software**: tools for generating, signing, and revoking digital certificates.

10. **Physical and virtual network interfaces**: network cards, controllers, and virtual adapters.

11. **Operating systems**: system-wide software for PCs, mobile devices, and servers.

12. **Routers, modems, and switches intended for connection to the internet**: network equipment for traffic transmission and switching.

13. **Microprocessors with security-related functionalities**: processors with hardware protection mechanisms (Annex III expressly excludes general-purpose microprocessors without security functions).

14. **Microcontrollers with security-related functionalities**: embedded microcontrollers with hardware protection mechanisms.

15. **Application-specific integrated circuits (ASIC) and field-programmable gate arrays (FPGA) with security-related functionalities**: special-purpose hardware circuits with built-in security functions.

16. **Smart home general-purpose virtual assistants**: general-purpose smart speakers and voice assistants for controlling a smart home.

17. **Smart home products with security functionalities**: smart door locks, video baby monitors, home security cameras, alarm systems (leak/fire sensors are mentioned in some secondary sources on 2025/2392, but not in the base text of Annex III — verify separately before relying on this example publicly).

18. **Connected toys**: toys covered by Directive 2009/48/EC (Toy Safety Directive) that have social interactive features (e.g. speaking or filming) **or** a location-tracking feature — not any internet-connected toy.

19. **Personal wearable health-monitoring devices**: general-purpose smartwatches, fitness trackers, and health monitors that are not covered by the Medical Device Regulation (MDR/IVDR), **and also** any personal wearable device intended for use by or for children — regardless of whether it has a health-monitoring function.

**3. Full list of Annex III Class II categories (Important products, Class II)**

**Class II** products perform fundamental perimeter-defence functions or provide deep isolation of computing processes. Compromising these systems leads to a complete compromise of the entire IT infrastructure.

**Class II** consists of 4 key categories:

1. **Hypervisors and container runtime systems**: virtualisation tools (e.g. VMware ESXi, Proxmox, Docker runtime, Kubernetes container engines).

2. **Firewalls**: software and hardware firewalls designed to filter network traffic.

3. **Intrusion detection and prevention systems (IDS/IPS)**: tools for monitoring and actively blocking network attacks.

4. **Tamper-resistant microprocessors and microcontrollers**: chips with specialised hardware protection against physical and electrical tampering.

**4. Full list of Annex IV critical products (Critical Products)**

Annex IV covers products whose compromise poses a threat to critical national infrastructure, the financial-payment system, or the EU's digital sovereignty.

The list of **critical products (Annex IV)** includes:

1. **Hardware devices with security boxes**: physical devices with a hardware-protected enclosure for cryptographic operations (e.g. Hardware Security Modules — HSM, payment POS terminals, digital tachographs).

2. **Smart meter gateways**: devices managing communication and data transmission in **electricity** smart-metering systems (Annex IV explicitly references the definition of a smart metering system under Directive (EU) 2019/944 — gas or heat supply is not covered), and also **other devices for advanced security purposes, including secure cryptoprocessing** — this second limb of Annex IV is often overlooked.

3. **Smartcards and similar devices, including secure elements (SE)**: hardware security chips, electronic passports, SIM/eSIM cards, and bank cards.

**5. The "Core Functionality" principle**

The Core Functionality principle, introduced by Implementing Regulation (EU) 2025/2392, provides that a product is subject to the heightened conformity assessment requirements of Annex III or IV only when its **core purpose/fundamental function** matches a description in one of those annexes.

**Component integration rule**: simply integrating a component that belongs to an important-product category (e.g. integrating a browser engine or an encryption module) into a larger product **does not turn** that entire larger product into an important product.

*Example from Commission clarifications*: a news mobile app integrates an embedded browser to open external links. Because the app's core function is displaying news, not providing web-browsing services, the news app itself remains in the **Default** category. A standalone web browser (e.g. Mozilla Firefox or Google Chrome), by contrast, is an **Important Class I** product.

**The same physical chip can land in a different class purely because of firmware.** Core Functionality is evaluated at the level of what actually ships — for the standalone microprocessor/microcontroller categories in Annex III Class I (items 13–14 above), that means the chip itself as sold, not its theoretical silicon capabilities. Take a general-purpose microcontroller manufactured with an on-chip secure element (hardware crypto accelerator, secure boot support) for use across several product lines. Flashed with firmware that only exposes basic sensor-reading and Wi-Fi telemetry, with the secure element left unused, the shipped product's core functionality is data collection — **Default**. The identical die, flashed with firmware that activates and exposes the secure element as the product's advertised function (sold as a standalone secure authentication microcontroller), now has a core functionality matching **Microcontrollers with security-related functionalities** (item 14) — **Important Class I**. Same silicon, two different CRA classes, because the firmware build decides what function actually ships. This is the same logic as the PLC/firewall case in section 8 below — it is not unique to microcontrollers, but it is where manufacturers reusing one hardware platform across product lines most often assume classification travels with the chip instead of with the firmware.

**6. Step-by-step algorithm for a manufacturer to determine a product's class**

To accurately determine its product's category, a manufacturer should work through the following 6 steps:

```
[Step 1: Qualify as a PDE and check exclusions (Art. 2)]
        |
        v
[Step 2: Determine core functionality]
        |
        v
[Step 3: Does the core functionality match Annex IV?]
   |-- YES --> CRITICAL PRODUCT (Annex IV)
   `-- NO
        |
        v
[Step 4: Does the core functionality match Annex III Class II?]
   |-- YES --> IMPORTANT CLASS II (Annex III)
   `-- NO
        |
        v
[Step 5: Does the core functionality match Annex III Class I?]
   |-- YES --> IMPORTANT CLASS I (Annex III)
   `-- NO
        |
        v
[Step 6: DEFAULT PRODUCT]
```

- **Step 1**: check whether the product meets the definition of a PDE (Article 3(1)) and whether an exclusion under Article 2 applies (e.g. MDR medical devices, UN R155 automotive, aviation, purely non-commercial open source).

- **Step 2**: determine the product's primary, core functionality based on its technical documentation and marketed purpose.

- **Step 3**: check against Annex IV (HSM, smart meter gateway, secure element). If yes — **Critical product**.

- **Step 4**: check against Annex III Class II (firewall, IDS/IPS, hypervisor, tamper-resistant MCU). If yes — **Important product, Class II**.

- **Step 5**: check against Annex III Class I (browser, password manager, antivirus, VPN, OS, router, smart lock, connected toy, wearable). If yes — **Important product, Class I**.

- **Step 6**: if the product does not match any listed item in Annex III or IV, it is classified as a **Default product**.

**7. Differences in conformity assessment procedures**

Depending on the product class, the CRA sets out different legal conformity-assessment modules (under Article 32 and Annex VIII):

<table>
<thead>
<tr class="header">
<th><strong>Product class</strong></th>
<th><strong>Permitted conformity assessment module</strong></th>
<th><strong>Notified body involvement / external certification</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Default</strong></td>
<td><strong>Module A</strong> (manufacturer's internal control / self-assessment).</td>
<td><strong>Not required</strong>. The manufacturer performs a risk assessment and signs the declaration itself.</td>
</tr>
<tr class="even">
<td><strong>Important Class I</strong></td>
<td><p><strong>Option 1</strong>: <strong>Module A</strong> (provided harmonised EU standards are applied in FULL).</p>
<p><strong>Option 2</strong>: <strong>Module B+C</strong> (EU-type examination) or <strong>Module H</strong> (full quality assurance).</p></td>
<td><strong>Conditionally mandatory</strong>. If harmonised standards do not exist, or are only partially applied, notified body involvement is <strong>mandatory</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Important Class II</strong></td>
<td><strong>Module B+C</strong> (EU-type examination) OR <strong>Module H</strong> (full quality assurance).</td>
<td><strong>MANDATORY</strong>. Self-assessment under Module A is <strong>not permitted</strong>, regardless of whether standards exist.</td>
</tr>
<tr class="even">
<td><strong>Critical</strong></td>
<td>Certification under a Cybersecurity Act scheme (Regulation (EU) 2019/881) at assurance level at least 'substantial' OR <strong>Module B+C / H</strong> under an implementing act.</td>
<td><strong>MANDATORY</strong>. An external security certificate or assessment by a conformity assessment body is required.</td>
</tr>
</tbody>
</table>

**8. Practical walkthrough of IoT devices by risk class**

To illustrate, consider four typical IoT products and the logic behind their regulatory classification:

**Smart light bulb**

- **Purpose**: lighting with remote on/off control via Wi-Fi/Zigbee.

- **Analysis**: performs no security functions, does not control physical access, does not match any item listed in Annex III/IV.

- **CRA class**: **Default**.

- **Procedure**: self-assessment (Module A).

**Industrial temperature sensor**

- **Purpose**: measuring temperature on a production line and transmitting data over Modbus/Ethernet.

- **Analysis**: if the sensor is a passive measuring device with no firewall, routing, or security-control functions, it does not fall under Annex III/IV.

- **CRA class**: **Default**.

- **Procedure**: self-assessment (Module A).

**Wi-Fi smart door lock / IP security camera**

- **Purpose**: controlling physical access to a premises, or video surveillance of a site.

- **Analysis**: its core functionality is providing physical and property security (smart home products with security functionalities). Falls under the Annex III Class I list.

- **CRA class**: **Important Class I**.

- **Procedure**: Module A (if harmonised standards exist and are fully applied) or Module B+C / H with notified body involvement.

**Industrial programmable logic controller (PLC) with firewall functionality**

- **Purpose**: controlling industrial processes with built-in perimeter defence (firewall/IDS).

- **Analysis**: if the device's core or equally weighted functionality is traffic filtering and network protection (firewall/IDS), the device qualifies under the higher risk category (Annex III Class II).

- **CRA class**: **Important Class II**.

- **Procedure**: mandatory third-party assessment — notified body (Module B+C or Module H).

**Conclusions**

Correctly identifying the risk class at the very start of product development is a critical step in business planning. For **Default**-category products, the compliance procedure is as simple as possible and is handled entirely in-house (Module A). For the **Important** and **Critical** categories, manufacturers need to budget for time and resources to work with notified bodies or go through European certification well in advance.
