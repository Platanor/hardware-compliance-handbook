**Practical FAQ on the Cybersecurity Act (CSA) and EUCC for hardware/IoT manufacturers**

**Do we, as an IoT hardware manufacturer, have to comply with the CSA?**
Not in the same sense as the CRA or RED. The CSA's Title III doesn't impose mandatory requirements on your product directly — it's the legal framework that lets the EU create certification *schemes* like EUCC. Whether you need to engage with it at all depends on whether a scheme adopted under it (like EUCC) has been made mandatory for your specific product category by other law, or whether a customer/procurement requirement asks for it voluntarily. For most IoT manufacturers today, the CRA and RED are the mandatory obligations; CSA/EUCC certification is currently a voluntary, market-driven option layered on top.

**Is EUCC the same thing as CE marking under the CRA?**
No. CE marking under the CRA is a mandatory conformity-assessment outcome tied to essential requirements in CRA Annex I. EUCC is a voluntary certification scheme (unless separately mandated) under a completely different regulation, evaluated against its own scheme-specific criteria at 'basic', 'substantial' or 'high' assurance levels. A product can carry CE marking under the CRA without ever touching EUCC, and — in principle — could pursue EUCC certification without that automatically satisfying CRA obligations, unless a specific legal cross-reference says a EUCC certificate creates presumption of conformity with the CRA (verify this doesn't exist by default — see [`eucc-certification.md`](eucc-certification.md)).

**What are the three assurance levels, in plain terms?**
'Basic' is the lightest — largely a documentation review, and the only level where manufacturer self-assessment (an EU statement of conformity) is permitted. 'Substantial' adds active testing that security functionality is correctly implemented and confirms there are no publicly known vulnerabilities. 'High' adds resistance testing against skilled, well-resourced attackers, including penetration testing — and can only be certified by a national authority or a specifically authorised body, not by self-assessment.

**Who actually issues an EUCC certificate?**
An accredited conformity assessment body (accredited by your national accreditation body under the same Regulation (EC) No 765/2008 framework used for CE-marking conformity assessment generally), or in some cases the national cybersecurity certification authority itself. For 'high' assurance level specifically, only the national authority, or a body with prior per-certificate approval or a general delegation from it, can issue the certificate.

**Where do complaints or disputes about a certificate go?**
First to the issuer of the certificate — or, if a conformity assessment body issued it under the 'high'-assurance delegation route, to the relevant national cybersecurity certification authority. If unresolved, natural and legal persons have a right to an effective judicial remedy before the courts of the Member State where that authority or body is located (CSA Articles 63–64).

**What penalties apply if something goes wrong with an EUCC certificate?**
There's no EU-wide fixed penalty figure — Article 65 leaves the actual rules to national law, only requiring that penalties be effective, proportionate and dissuasive. This is the same structural pattern as RED's Article 46 (see [`../red/penalties-enforcement.md`](../red/penalties-enforcement.md)) and different from the CRA, which does set explicit EU-wide maximum fines.

**Does ENISA "run" EUCC?**
ENISA prepares candidate schemes (including originally EUCC) and maintains the public website listing schemes, certificates and EU statements of conformity (Art. 50), but it does not issue certificates itself and does not supervise conformity assessment bodies directly — that's the job of each Member State's national cybersecurity certification authority. ENISA's role here is preparatory and coordinating, not operational/enforcement.

**Where do I find the actual legal text?**
[`../primary-sources/cybersecurity-act-eu-2019-881.md`](../primary-sources/cybersecurity-act-eu-2019-881.md) covers the CSA framework itself (complete, Articles 1–69 plus the Annex). It does **not** include the separate implementing act that defines EUCC's own technical scheme details — that source still needs to be added to this knowledge base before citing EUCC-specific technical requirements as fact.
