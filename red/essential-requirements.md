**RED essential requirements: cybersecurity provisions of Article 3, scope, and harmonised standards**

**The two tiers of Article 3**

Article 3 of Directive 2014/53/EU sets essential requirements in two structurally different tiers.

**Article 3(1)–(2) — unconditional, apply to all radio equipment:**

- (1)(a) Protection of health and safety of persons and domestic animals, and protection of property — incorporating the objectives of Directive 2014/35/EU, but with no voltage limit applying.
- (1)(b) An adequate level of electromagnetic compatibility, as set out in Directive 2014/30/EU.
- (2) Effective use and support for efficient use of the radio spectrum, to avoid harmful interference.

**Article 3(3) — category-gated, apply only where a delegated act names the categories:**

Article 3(3) lists nine requirements, (a) through (i). None of them applies to any product until the European Commission adopts a delegated act specifying which categories or classes of radio equipment are concerned by each. This repository's focus is on the three that address cybersecurity risk and have been activated:

| Point | Requirement (verbatim, Art. 3(3)) | Activated by |
| --- | --- | --- |
| **(d)** | "radio equipment does not harm the network or its functioning nor misuse network resources, thereby causing an unacceptable degradation of service" | Delegated Regulation (EU) 2022/30, Art. 1(1) |
| **(e)** | "radio equipment incorporates safeguards to ensure that the personal data and privacy of the user and of the subscriber are protected" | Delegated Regulation (EU) 2022/30, Art. 1(2) |
| **(f)** | "radio equipment supports certain features ensuring protection from fraud" | Delegated Regulation (EU) 2022/30, Art. 1(3) |

The other six points — (a) interworking with common chargers, (b) interworking via networks, (c) connection to interfaces, (g) emergency-services access, (h) accessibility, (i) software-combination compliance — remain dormant. No delegated act has activated them as of this repository's last verification date. Citing "Article 3(3)" without specifying which point, and confirming that point has been activated, does not establish an actual obligation.

**What Delegated Regulation (EU) 2022/30 actually scopes each requirement to**

The delegated act does not apply (d), (e), and (f) to all radio equipment uniformly — each point has its own trigger, set out in its Article 1:

- **Point (d), network protection** — applies to any **internet-connected radio equipment**: equipment capable of communicating over the internet itself, whether directly or via other equipment.
- **Point (e), personal data and privacy** — applies to internet-connected radio equipment (as above), **plus** radio equipment designed or intended exclusively for childcare, radio equipment covered by the Toy Safety Directive (2009/48/EC), and wearable radio equipment (worn on, strapped to, or hung from the body or clothing) — but only where that equipment is capable of processing personal data (as defined in the GDPR, Article 4(1)) or traffic/location data (as defined in the ePrivacy Directive, Article 2(b)(c)).
- **Point (f), fraud protection** — applies to internet-connected radio equipment that enables the holder or user to transfer money, monetary value, or virtual currency.

**Carve-outs.** Radio equipment already covered by the Medical Devices Regulation (EU 2017/745) or the In Vitro Diagnostic Medical Devices Regulation (EU 2017/746) is excluded from all three points. Equipment covered by civil-aviation rules (EU 2018/1139), vehicle type-approval rules (EU 2019/2144), or electronic road-toll interoperability rules (EU 2019/520) is excluded from points (e) and (f) only.

**Application date: 1 August 2025, not 2024**

Delegated Regulation (EU) 2022/30 originally set its own application date at 1 August 2024 (Article 3). Delegated Regulation (EU) 2023/2444 pushed that back to **1 August 2025**, to give CEN and Cenelec (the European standardisation bodies) more time to draft harmonised standards of adequate quality for what the Commission itself describes as a genuinely complex, first-of-its-kind standardisation task. The same amending act also corrected a drafting error in Article 1(2) of the original text (the description of what "processing" data means for point (e)). **1 August 2025 is the date that matters — anything citing 1 August 2024 is citing the superseded date.**

**Harmonised standards: EN 18031-1/-2/-3, and why the presumption of conformity is partial**

Commission Implementing Decision (EU) 2025/138 (published in the OJ on 30 January 2025) added references to three harmonised standards to the list conferring presumption of conformity under RED:

- **EN 18031-1:2024** — common security requirements for internet-connected radio equipment, supporting point (d).
- **EN 18031-2:2024** — common security requirements for internet-connected, childcare, toy, and wearable radio equipment, supporting point (e).
- **EN 18031-3:2024** — common security requirements for internet-connected radio equipment processing virtual money or monetary value, supporting point (f).

**These standards were published with restrictions — a manufacturer applying them does not automatically get a full presumption of conformity.** The Commission identified specific gaps during its assessment (Implementing Decision (EU) 2025/138, recitals 5–8 and Annex):

1. **"Rationale" and "guidance" sections confer no presumption.** These standards contain sections labelled "rationale" (justifying why a risk needs addressing) and "guidance" (examples of possible mitigations). Neither sets out an actual specification, so neither confers a presumption of conformity — even though a manufacturer might read them as if they did.
2. **The "no password" escape hatch (all three standards, clauses 6.2.5.1–6.2.5.2).** Each standard lets a manufacturer implement a configuration where the user is allowed not to set or use any password at all. Applying that option means the standard does **not** confer a presumption of conformity — the Commission judged that authentication risk isn't properly addressed if this option is used.
3. **Toy and childcare access control (EN 18031-2 only, clauses 6.1.3–6.1.6).** These clauses offer several access-control implementation categories (role-based, discretionary, mandatory access control, or others). Where parental or guardian access control is not actually ensured, the standard does not confer presumption of conformity for point (e).
4. **Secure updates for payment-capable equipment (EN 18031-3 only, clause 6.3.2.4).** The standard's assessment criteria for secure updates (based on digital signatures, secure communication, access control, or others) were judged insufficient on their own for equipment handling financial assets — none of the listed methods alone is considered adequate, so this clause does not confer presumption of conformity either.

**Practical consequence:** applying EN 18031-1/-2/-3 gets a manufacturer real credit toward compliance, but only for the parts of the standard the Commission accepted without restriction. Where a product falls into one of the four gaps above, self-declared presumption of conformity is not available for that part, and a notified body (Module B+C or H) is needed instead — even though, on paper, "a harmonised standard exists." This is the trap flagged in [`cra-red-ce-marking-guide.md`](../cra-red-ce-marking-guide.md): don't assume the "simple path" is automatically open just because a standard reference has been published.

**How this interacts with the CRA's own Annex I**

CRA Annex I, Part I, point 2(d) requires products to "ensure protection from unauthorised access by appropriate control mechanisms, including but not limited to authentication, identity or access management systems, and report on possible unauthorised access." This is broader and more open-ended than RED's activated points — RED's cybersecurity requirements are scoped to specific product categories and specific harms (network harm, privacy, fraud), while the CRA's requirement applies (subject to its own risk-based chapeau) across the full range of products with digital elements. A device meeting RED's activated requirements has not automatically satisfied the CRA's Annex I — the two assessments, while related in subject matter, are legally separate exercises until RED's cybersecurity delegated act is repealed in favour of the CRA framework.
