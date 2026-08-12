**Directive 2014/53/EU (Radio Equipment Directive, RED) and its cybersecurity provisions: a comprehensive analysis of scope, requirements, and institutional architecture**

**Background, regulatory context, and objective**

Directive 2014/53/EU of the European Parliament and of the Council of 16 April 2014, known as the Radio Equipment Directive (RED), establishes the regulatory framework for making radio equipment available on the EU market. It entered into force on 21 June 2014 and became applicable on 13 June 2016, repealing the earlier Directive 1999/5/EC (the "R&TTE Directive").

RED's original purpose was not cybersecurity. Its core essential requirements (Article 3(1)–(2)) cover health and safety, electromagnetic compatibility, and efficient use of the radio spectrum — the same concerns as its 1999 predecessor. What makes RED relevant to hardware manufacturers working through cybersecurity obligations today is a second, narrower set of essential requirements: Article 3(3), points (d), (e), and (f), covering network protection, personal-data and privacy protection, and fraud protection. These three points sat legally dormant for years — Article 3(3) applies "within certain categories or classes" only once the European Commission names those categories in a delegated act. That act, Commission Delegated Regulation (EU) 2022/30, did exactly that, and its essential requirements have been binding since **1 August 2025**.

**Why this matters alongside the CRA:** for any connected device with a radio interface (Wi-Fi, Bluetooth, cellular, LoRa, etc.), RED's cybersecurity requirements are a live, binding obligation *today* — running years ahead of the Cyber Resilience Act's full application date of 11 December 2027. A manufacturer cannot treat "cybersecurity regulation" as something that starts in 2027; if the product has a radio module, part of it already applies.

**Key dates, legal deadlines, and the application regime**

| **Event/regulatory milestone** | **Legal date** | **Regulatory content and obligations** |
| --- | --- | --- |
| **RED published in the Official Journal** | 22 May 2014 (OJ L 153) | The text of Directive 2014/53/EU is fixed. |
| **RED enters into force** | 21 June 2014 | Twentieth day following publication (Art. 51). |
| **RED becomes applicable** | 13 June 2016 | Member States apply their transposing national laws from this date (Art. 49). Directive 1999/5/EC repealed. |
| **Delegated Regulation (EU) 2022/30 adopted** | 29 October 2021 | Names the categories of radio equipment subject to Art. 3(3)(d)(e)(f) — published in OJ 12 January 2022. |
| **Cybersecurity essential requirements become binding** | **1 August 2025** | Art. 3(3)(d)(e)(f) apply to internet-connected, childcare, toy, and wearable radio equipment (as scoped by 2022/30). Original date was 1 August 2024; pushed back by Delegated Regulation (EU) 2023/2444 to give standards bodies more time. |
| **EN 18031-1/-2/-3 published in OJ, with restrictions** | 30 January 2025 (Implementing Decision (EU) 2025/138) | Harmonised standards enabling self-declared presumption of conformity become available — but not for every product, see [`essential-requirements.md`](essential-requirements.md) for the restrictions. |

**Subject matter of regulation and scope**

RED applies to "radio equipment" — defined in Article 2(1) as any electrical or electronic product that intentionally emits and/or receives radio waves for radio communication or radiodetermination, or that must be completed with an accessory (such as an antenna) to do so. This is a broad definition: it covers finished consumer products, but the directive does not distinguish between a product's radio and non-radio functions — all aspects and parts of a product meeting this definition fall within scope (Delegated Regulation (EU) 2022/30, recital 8).

RED's essential requirements are structured in two tiers:

- **Article 3(1)–(2)** — unconditional, apply to *all* radio equipment: health and safety, electromagnetic compatibility, and efficient/effective use of the radio spectrum to avoid harmful interference.
- **Article 3(3), points (a)–(i)** — nine additional requirements (interworking with accessories/networks, network protection, privacy, fraud protection, emergency-services access, accessibility, software-combination compliance) that apply only to categories or classes of equipment the Commission names in a delegated act. Of these nine, only **(d)**, **(e)**, and **(f)** — the cybersecurity-relevant ones — have been activated, by Delegated Regulation (EU) 2022/30.

Full detail on what each activated requirement covers, and which product categories are in scope, is in [`essential-requirements.md`](essential-requirements.md).

**Who must comply, and how RED divides responsibility**

RED assigns obligations to the same three economic-operator roles used across EU product legislation:

- **Manufacturer** — designs, produces, and markets radio equipment under its own name or trademark; bears the core compliance obligations (Article 10).
- **Importer** — places third-country radio equipment on the EU market (Article 12).
- **Distributor** — makes equipment available on the market without altering it (Article 13).

An importer or distributor that places equipment on the market under its own name/trademark, or modifies equipment already on the market in a way that could affect compliance, is treated as the manufacturer and takes on the manufacturer's full obligations (Article 14). Full detail in [`obligations-by-role.md`](obligations-by-role.md).

**Conformity assessment and presumption of conformity**

Manufacturers demonstrate compliance via one of three procedures (Article 17, Annexes II–IV): internal production control (**Module A**, self-assessment), EU-type examination followed by conformity to type (**Module B+C**), or full quality assurance (**Module H**). Which procedure is available depends on whether the manufacturer has applied a relevant harmonised standard in full — where one exists and is applied, self-assessment (Module A) is available even for Article 3(2)–(3) requirements; where none exists, or the standard is only partially applied, only the two more demanding procedures (B+C or H) are open (Article 17(3)–(4)).

Where a manufacturer complies with a harmonised standard whose reference has been published in the Official Journal, the product is **presumed to conform** to the essential requirements that standard covers (Article 16). This presumption is not automatic for RED's cybersecurity requirements — see the restrictions on EN 18031-1/-2/-3 in [`essential-requirements.md`](essential-requirements.md).

**Relationship to the CRA and the expected transition**

RED and the CRA are not competing regulations covering the same ground by accident — they are the same regulatory intent arriving in two waves. The CRA's essential cybersecurity requirements (Annex I) already cover everything RED's Article 3(3)(d)(e)(f) requires. Once the CRA is fully in force (11 December 2027), RED's cybersecurity delegated act is expected to be repealed and absorbed into the CRA framework. That repeal has **not** happened yet. Until it does, a radio-connected product with digital elements must satisfy both frameworks in parallel: RED's cybersecurity requirements, binding since 1 August 2025, and the CRA's phased-in obligations. See [`relationship-to-other-eu-law.md`](../relationship-to-other-eu-law.md) for the full picture of how RED, the CRA, NIS2, and the Cybersecurity Act interact, and [`cra-red-ce-marking-guide.md`](../cra-red-ce-marking-guide.md) for the practical step-by-step path through both.

**Structural anatomy of the directive**

Directive 2014/53/EU has 75 recitals, 7 chapters (52 articles), and 8 annexes.

- **Chapter I** (Articles 1–9) — general provisions: scope, definitions, essential requirements (Article 3), registration, free movement.
- **Chapter II** (Articles 10–15) — obligations of economic operators.
- **Chapter III** (Articles 16–18) — conformity of radio equipment: presumption of conformity, conformity assessment procedures, EU declaration of conformity.
- **Chapter IV** (Articles 22–38) — notification of conformity assessment bodies (notified bodies).
- **Chapter V** (Articles 39–43) — CE marking, market surveillance, control of equipment entering the EU market, safeguard procedures.
- **Chapter VI** (Articles 44–45) — delegated acts, implementing acts, and the committee procedure.
- **Chapter VII** (Articles 46–52) — final and transitional provisions: penalties (Article 46), review and reporting, transposition, repeal of Directive 1999/5/EC, entry into force.

**Points of practical friction for manufacturers**

**The "activated by delegated act" structure catches people out.** Citing Article 3(3) alone says nothing about what a given product must do — six of its nine points ((a),(b),(c),(g),(h),(i)) remain dormant with no delegated act yet naming categories for them. Only (d), (e), (f) are live, and only for the categories Delegated Regulation (EU) 2022/30 names: internet-connected radio equipment (for (d) and, where it processes personal data, for (e)); childcare, toy, and wearable radio equipment (for (e)); and internet-connected equipment enabling money/virtual-currency transfer (for (f)).

**Module vendors and integrators.** A third-party radio module or System-on-Module (SOM) shipped as a bare component requiring integration is typically not itself subject to these requirements — module vendors often mark this "N/A" in their own declaration. Responsibility shifts to whoever integrates the module into a finished product; a "certified" radio module does not certify the final device.

**Not a consolidated text.** The primary source stored in this repository is the original 2014 act, not a consolidated version — RED has since been touched by Directive (EU) 2018/1972 and Directive (EU) 2022/2380 (common charger), neither reflected in the original text. Article 3(3)(d)(e)(f), the provisions this repository focuses on, are unaffected by those amendments.
