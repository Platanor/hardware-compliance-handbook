**EUCC (EU Common Criteria) certification — what the Cybersecurity Act framework tells us, and what still needs its own primary source**

**⚠️ Scope note before reading this file:** EUCC is a specific European cybersecurity certification scheme adopted **under** the framework set up by the Cybersecurity Act (Regulation (EU) 2019/881), via a separate Commission implementing act (an Implementing Regulation adopted pursuant to Article 49(7) of the CSA). **That implementing act — which contains the EUCC scheme's actual technical requirements, evaluation methodology, and assurance-level mapping — is not yet mirrored in this knowledge base's `primary-sources/` folder.** Everything below that is sourced to the CSA itself (Regulation (EU) 2019/881) is reliable; anything about EUCC-specific mechanics beyond the general framework should be verified against the EUCC implementing act directly before you rely on it for a compliance decision. Flagging this explicitly rather than guessing at scheme-specific detail we haven't fact-checked.

**What we can say reliably, from the CSA itself (Regulation (EU) 2019/881)**

EUCC is the practical instance of the general mechanism set out in Title III of the CSA:

1. **How a scheme like EUCC comes into existence** (Art. 47–49): the Commission publishes a rolling work programme identifying candidate areas for certification; the Commission or the ECCG can request ENISA to prepare a candidate scheme; ENISA drafts it through a formal, open, transparent stakeholder consultation and close cooperation with the ECCG; the Commission then adopts the scheme through an implementing act under the examination procedure (Art. 66(2)).

2. **What any adopted scheme, including EUCC, must specify** (Art. 54(1)): scope (which product/service/process types are covered), the standards/technical specifications referenced, applicable assurance level(s), whether self-assessment is permitted, requirements for conformity assessment bodies, evaluation criteria and methods, certificate content/format, validity period, and vulnerability-handling rules, among the other elements listed in Art. 54(1) — see the [primary source](../primary-sources/cybersecurity-act-eu-2019-881.md#article-54--elements-of-european-cybersecurity-certification-schemes) for the full 22-point list.

3. **Assurance levels available to it** (Art. 52): 'basic', 'substantial', or 'high' — EUCC, as a scheme aimed at ICT products (historically building on the pre-existing SOG-IS mutual-recognition Common Criteria arrangement among a subset of Member States), is understood to concentrate at the higher assurance levels ('substantial'/'high') rather than 'basic', reflecting its Common Criteria lineage — **verify this against the EUCC implementing act itself rather than citing this knowledge base for the specific assurance-level mapping.**

4. **Voluntary status, unless other law says otherwise** (Art. 56(2)): EUCC certification is voluntary by default. It becomes mandatory for a given product category only if a separate piece of Union or Member State law explicitly requires it. Check current legislation for your specific product category rather than assuming either voluntary or mandatory status.

5. **Who can issue an EUCC certificate** (Art. 56(4)–(6)): for 'basic'/'substantial' assurance, accredited conformity assessment bodies (see the [Annex requirements](../primary-sources/cybersecurity-act-eu-2019-881.md#annex--requirements-to-be-met-by-conformity-assessment-bodies)); for 'high' assurance, only the national cybersecurity certification authority, or a conformity assessment body with prior per-certificate approval or a general delegation from that authority.

6. **National routing** (Art. 58): each Member State designates its own national cybersecurity certification authority, responsible for supervising EUCC-issuing bodies in its territory, handling complaints, and enforcing penalties under national law (Art. 65) — there is no single EU-wide enforcement body for EUCC.

**How this could matter for a CRA/RED-in-scope IoT manufacturer**

- **A voluntary EUCC certificate is not, by default, a substitute for CRA conformity assessment.** The CRA and RED impose their own mandatory essential requirements and their own conformity-assessment routes (self-assessment or notified body, depending on product risk class). A CSA scheme certificate can only be used to demonstrate presumption of conformity with another law's requirements where that other law explicitly says so (CSA Art. 54(3)) — check whether the CRA, its delegated/implementing acts, or the relevant harmonised standards make any such cross-reference to EUCC. As of this file's last check, no confirmed CRA-to-EUCC presumption-of-conformity link has been verified in this knowledge base.
- **Certification cost/effort should be weighed against actual market or contractual demand.** Since EUCC is voluntary for most product categories today, the practical driver for pursuing it is usually a customer requirement (e.g., a public-sector procurement clause, or a security-conscious enterprise buyer) rather than a legal mandate — unlike CRA/RED essential requirements, which apply regardless of customer preference.
- **Component-level vs. finished-product certification is a Common Criteria–lineage nuance** (chips, secure elements, and similar components have historically been certified separately from the finished device under Common Criteria/SOG-IS schemes) — if your product incorporates a pre-certified secure component, that does not automatically make the finished IoT device EUCC-certified; **this is a general Common Criteria pattern worth checking against the actual EUCC implementing act, not a claim sourced to the CSA text itself.**

**What to do next if EUCC becomes relevant to a specific deal or product**

1. Pull the actual EUCC implementing act (a Commission Implementing Regulation adopted under CSA Art. 49(7)) directly from EUR-Lex and verify assurance-level mapping, scope, and evaluation methodology before making any claim to a client.
2. Check the ENISA certification website (CSA Art. 50 requires ENISA to maintain one) for the current list of accredited/notified conformity assessment bodies for EUCC.
3. Confirm with the relevant national cybersecurity certification authority (CSA Art. 58) whether any national scheme it previously operated has ceased to have effect in favour of EUCC (CSA Art. 57).

**Where to find the primary text**

[`../primary-sources/cybersecurity-act-eu-2019-881.md`](../primary-sources/cybersecurity-act-eu-2019-881.md) — the CSA framework text (complete). The EUCC scheme's own implementing act is **not yet in this knowledge base** — treat any EUCC-specific technical claim not attributed to the CSA itself as unverified until that source is added.
