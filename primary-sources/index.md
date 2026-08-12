# Primary sources — official text

This folder contains the **full official text** of the regulations and related acts that the analysis in the rest of this repository is based on. Unlike the other documents (`overview.md`, `definitions.md`, etc. — our **processed** version: shorter, structured, easy to read), these files are the **raw, unmodified text from official sources**.

**Why a separate folder:**

- For a human — to check a quote directly, without an intermediary.
- For LLM/RAG pipelines — so the model can ground its answer in the original wording of an article rather than our paraphrase. The processed files are better for quickly understanding a topic; these files are the source of truth for exact quotes.

**Every file is immutable.** We do not edit or translate the text of these acts — we only add a provenance header (where it came from, when it was retrieved, how it was converted). If an act is later amended, a new file is added alongside it and the old one is marked superseded; the existing text is never rewritten.

## Contents

| File | Instrument | Status |
|---|---|---|
| [cra-regulation-eu-2024-2847.md](cra-regulation-eu-2024-2847.md) | **Regulation (EU) 2024/2847 — Cyber Resilience Act.** All articles + Annexes I–VIII | Official (EUR-Lex), complete |
| [cra-standardisation-request-m606-c-2025-618.md](cra-standardisation-request-m606-c-2025-618.md) | **C(2025) 618 final — CRA standardisation request (M/606)** to CEN/Cenelec/ETSI, incl. Annexes I and II | Official, complete |
| [red-directive-2014-53-eu.md](red-directive-2014-53-eu.md) | **Directive 2014/53/EU — Radio Equipment Directive.** All 52 articles + Annexes I–VIII | Official (EUR-Lex) — **original 2014 text, not consolidated** with later amendments |
| [red-delegated-regulation-eu-2022-30.md](red-delegated-regulation-eu-2022-30.md) | **Delegated Regulation (EU) 2022/30** — activates RED Art. 3(3)(d)(e)(f) cybersecurity requirements | Official (EUR-Lex), original act — see amendment below |
| [red-delegated-regulation-eu-2023-2444-amending.md](red-delegated-regulation-eu-2023-2444-amending.md) | **Delegated Regulation (EU) 2023/2444** — amends 2022/30's date of application | Official (EUR-Lex), complete |
| [red-implementing-decision-eu-2025-138-en-18031.md](red-implementing-decision-eu-2025-138-en-18031.md) | **Implementing Decision (EU) 2025/138** — cites EN 18031-1/-2/-3 in the OJ, with restrictions | Official (EUR-Lex), complete |
| [nis2-directive-eu-2022-2555.md](nis2-directive-eu-2022-2555.md) | **Directive (EU) 2022/2555 — NIS2.** Articles 1–46 + Annexes I–II | Official (EUR-Lex) — enacting terms and Annexes I–II complete; recitals only partially captured (first ~57 of 139); Annex III (correlation table) not captured |
| [cybersecurity-act-eu-2019-881.md](cybersecurity-act-eu-2019-881.md) | **Regulation (EU) 2019/881 — Cybersecurity Act (CSA).** Articles 1–69 + Annex | Official (EUR-Lex), enacting terms and Annex complete; recitals not captured |

## Right to reproduce

These are official texts of EU acts (Official Journal), not our own authored content — the CC BY 4.0 license in the repository's `README.md` applies to **our** analytical files, not to these primary sources. Official EU legislative text may be reproduced provided the source is acknowledged (the Commission's document-reuse policy) — the source and retrieval date are given in each file's header.

The legal basis for this is **Commission Decision 2011/833/EU** on the reuse of Commission documents, as reflected in the [EUR-Lex legal notice](https://eur-lex.europa.eu/content/legal-notice/legal-notice.html): legal texts published on EUR-Lex may be reproduced for both commercial and non-commercial purposes, provided the source is acknowledged, the content is not altered in a way that distorts its original meaning, and the copy is not presented as the official/authentic version — only the printed or authenticated electronic Official Journal is authentic. That third condition is why every file in this folder carries a provenance header noting it is **not** the authoritative version and pointing to the original EUR-Lex source.

## What's not here

Some sources referenced in our analysis are paywalled or otherwise unavailable, so they are not included:

- **EN 18031-1/-2/-3:2024** — the standard text itself is sold by the national CEN/Cenelec members. Only the decision citing it in the OJ (the file above) is free.
- **Consolidated RED** — the original 2014 Directive is stored here; a consolidated version reflecting the 2018 and 2022 amendments has not been retrieved.
- **IEEE 802.1AR-2018**, **TCG DICE specifications** — publications of the respective organisations.

Where a claim in our analytical files rests on one of these sources, that is stated explicitly rather than presented as verified against the primary text.
