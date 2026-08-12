**Cybersecurity Act (CSA) — overview: what it is, and how it differs from CRA, RED and NIS2**

**What it actually is**

The Cybersecurity Act — Regulation (EU) 2019/881 — is the odd one out among the four regulations covered by this knowledge base, because it does two structurally unrelated things in one legal act (Art. 1(1)):

1. It gives **ENISA** (the EU Agency for Cybersecurity) its permanent mandate, objectives, tasks and governance structure (Titles I–II, Articles 1–45).
2. It establishes the **European cybersecurity certification framework** — the legal mechanism through which the EU can create voluntary (or, later, mandatory) certification schemes for ICT products, services and processes (Title III, Articles 46–65).

Most of what a hardware/IoT manufacturer needs from this regulation lives in Title III — specifically the mechanism that produced the **EUCC (EU Common Criteria) scheme**, the first cybersecurity certification scheme adopted under this framework. See [`eucc-certification.md`](eucc-certification.md) for the EUCC specifically.

**Key dates**

| Date | What happened |
| --- | --- |
| 17 April 2019 | Regulation (EU) 2019/881 adopted |
| 27 June 2019 | Entry into force (twentieth day after OJ publication); Regulation (EU) No 526/2013 repealed, ENISA re-established under this Regulation |
| 28 June 2020 | Deadline for the Commission's first Union rolling work programme for certification (Art. 47(5)) |
| 28 June 2021 | Articles 58, 60, 61, 63, 64 and 65 (national authorities, accreditation, notification, complaints, judicial remedy, penalties) became applicable — a delayed application date relative to the rest of the Regulation |
| 31 December 2023 | Deadline for the Commission's first assessment of whether existing schemes should become mandatory (Art. 56(3)) |
| 28 June 2024 | First five-yearly evaluation of ENISA and of the Title III certification framework due (Art. 67) |

**Subject matter and scope**

Unlike CRA and RED, which regulate *products* directly through mandatory essential requirements, and unlike NIS2, which regulates *organisations*, the CSA's Title III does not itself impose mandatory requirements on any product or entity. It builds **infrastructure**: a framework under which the Commission can adopt specific certification *schemes* (via implementing acts, Art. 49(7)), and each scheme decides its own scope, assurance levels, and whether certification under it is voluntary or mandatory.

**Structural anatomy**

- Title I — General provisions (Arts. 1–2): scope and definitions.
- Title II — ENISA (Arts. 3–45): mandate, tasks, governance (Management Board, Executive Board, Executive Director, Advisory Group, Stakeholder Cybersecurity Certification Group, National Liaison Officers Network), budget, staff.
- Title III — Cybersecurity certification framework (Arts. 46–65): the framework itself, the Union rolling work programme, scheme preparation/adoption/review, security objectives, assurance levels, conformity self-assessment, scheme elements, national certification authorities, conformity assessment bodies, the European Cybersecurity Certification Group (ECCG), complaints, judicial remedy, penalties.
- Title IV — Final provisions (Arts. 66–69): committee procedure, evaluation, repeal/succession, entry into force.
- One Annex: requirements for conformity assessment bodies (accreditation criteria).

**Relationship to CRA, RED and NIS2**

- **Voluntary by default, unlike CRA/RED:** cybersecurity certification under a scheme adopted pursuant to this Regulation is voluntary "unless otherwise specified by Union or Member State law" (Art. 56(2)). The CRA and RED impose mandatory essential requirements and mandatory CE-marking conformity assessment on in-scope products; a CSA scheme like EUCC does not impose anything on a manufacturer unless another piece of law separately makes it mandatory, or the manufacturer chooses to certify voluntarily (e.g., for a customer requirement or a competitive differentiator).
- **A certificate can feed into a CRA/RED presumption of conformity — but only if specific legislation says so.** Article 54(3) allows a certificate or EU statement of conformity issued under a CSA scheme to be used to demonstrate presumption of conformity with another legal act's requirements, **where that other legal act explicitly provides for it.** As of this writing, no such cross-reference from the CRA or RED to a CSA scheme has been confirmed in this knowledge base — check the current state of any implementing acts before assuming EUCC certification substitutes for CRA/RED conformity assessment.
- **No EU-wide fixed penalty figure**, similar to RED and unlike CRA — Article 65 leaves penalties for infringements of Title III to national law, only requiring that they be "effective, proportionate and dissuasive." See [`../red/penalties-enforcement.md`](../red/penalties-enforcement.md) for the equivalent RED discussion.
- **Regulates neither products nor organisations directly — it regulates a certification *mechanism*.** This is different from all three other regulations in this knowledge base and is the most common source of confusion: the CSA itself does not tell you what to build or how to run your company; it tells you how a certification scheme comes into existence and what it must guarantee if you choose (or are required by other law) to use it.
- **ENISA's role is a genuine cross-cutting thread.** The same Agency established here (Title II) also has explicit tasks under NIS2 (see [`../nis2/overview.md`](../nis2/overview.md)) — supporting the CSIRTs network, preparing threat landscape reports, and assisting Member States. It is the same institutional actor across multiple regulations in this knowledge base, even though its ENISA-specific mandate sits in this Regulation.

**Practical friction points**

- **"Certified under the CSA" is not a single fact — check which scheme, and which assurance level.** A scheme adopted under this framework can offer three assurance levels (basic/substantial/high, Art. 52), each with different evaluation depth. A "basic" certificate is a much lighter claim than a "high" one — don't treat certification as binary.
- **Self-assessment exists here too, but only at the lowest tier.** Article 53 permits manufacturer/provider self-assessment (EU statement of conformity) only for products at assurance level "basic" — structurally similar to the CRA's self-assessment route for Default-class products, but a separate legal mechanism under a separate regulation.
- **Don't assume a scheme is mandatory.** The Commission periodically assesses (at least every two years from December 2023) whether specific schemes should become mandatory through other Union law (Art. 56(3)) — this is a live, evolving question, not settled once and for all.

**Where to find the primary text**

[`../primary-sources/cybersecurity-act-eu-2019-881.md`](../primary-sources/cybersecurity-act-eu-2019-881.md) — full enacting terms (Articles 1–69) and the Annex on conformity assessment body requirements. Recitals were not captured in this mirror; consult EUR-Lex directly if you need a recital.
