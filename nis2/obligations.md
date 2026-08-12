**NIS2 obligations: governance, the Article 21 risk-management measures, and the essential/important supervisory split**

**Governance (Article 20) — the obligation that names the board, not just "the organisation"**

Unlike the CRA and RED, which place obligations on "the manufacturer" as an abstract legal person, NIS2 explicitly reaches into corporate governance:

- **Management bodies of essential and important entities must approve the cybersecurity risk-management measures the entity takes**, oversee their implementation, and **can be held personally liable for the entity's infringements of Article 21**. This is without prejudice to Member States' own national liability rules for public institutions and public servants.
- Members of management bodies must undergo training on cybersecurity risk identification and assessment; entities are encouraged (not mandated) to offer similar training to employees generally.

**Practical consequence:** for an essential or important entity, cybersecurity risk management is not a delegable technical function that stays entirely within an IT or security team — the board has to formally sign off on it and can be personally on the hook if it doesn't.

**Cybersecurity risk-management measures (Article 21) — the substantive obligation**

Entities must take "appropriate and proportionate technical, operational and organisational measures" to manage risks to their network and information systems, based on an **all-hazards approach**, taking into account state-of-the-art practice, relevant standards, and cost of implementation, scaled to the entity's risk exposure, size, and the likelihood/severity of incidents.

The measures must include **at least** these ten elements (Art. 21(2)):

1. Policies on risk analysis and information system security
2. Incident handling
3. Business continuity (backup management, disaster recovery) and crisis management
4. **Supply chain security**, including security-related aspects of relationships with direct suppliers and service providers
5. Security in network/information-system acquisition, development and maintenance, including vulnerability handling and disclosure
6. Policies and procedures to assess the effectiveness of cybersecurity risk-management measures
7. Basic cyber hygiene practices and cybersecurity training
8. Policies and procedures on the use of cryptography and, where appropriate, encryption
9. Human resources security, access control policies, and asset management
10. Use of multi-factor authentication or continuous authentication, secured voice/video/text communications, and secured emergency communication systems, where appropriate

**On supply-chain security specifically (Art. 21(2)(d) and 21(3)):** when deciding what supply-chain measures are appropriate, entities must take into account vulnerabilities specific to each direct supplier/service provider, the overall quality of their products and cybersecurity practices (including their own secure-development procedures), and the outcome of any EU-level coordinated critical-supply-chain risk assessments carried out under Article 22. This is the clause that gives NIS2 real reach into hardware/software suppliers of NIS2-regulated entities, even where the supplier itself is not directly in scope of NIS2.

If an entity finds it doesn't comply with these measures, it must take corrective action "without undue delay" (Art. 21(4)).

**By 17 October 2024**, the Commission was to adopt implementing acts specifying the technical/methodological detail of these measures for a named list of digital-infrastructure-adjacent providers (DNS providers, TLD registries, cloud/data-centre/CDN providers, managed and managed-security service providers, online marketplaces/search engines/social-networking platforms, trust service providers) — with the option to extend similar implementing detail to other entity types.

**Supervision: essential entities vs. important entities (Articles 32-33) — the core structural distinction**

This is the aspect of NIS2 most likely to be misdescribed if essential and important entities are treated as interchangeable:

| | **Essential entities (Art. 32)** | **Important entities (Art. 33)** |
| --- | --- | --- |
| **Supervision model** | **Proactive** — competent authorities can inspect regardless of any known problem | **Reactive (ex post)** — action taken "where necessary," triggered by evidence, indication, or information of alleged non-compliance |
| **Supervisory powers** | On-site inspections, off-site supervision including **random checks**, **regular and targeted** security audits, ad hoc audits, security scans, information/document requests | On-site/off-site supervision, **targeted (not regular)** security audits, security scans, information/document requests |
| **Enforcement powers** | Warnings, binding instructions, cease-and-desist, compliance orders, orders to inform affected recipients, orders to implement audit recommendations, **power to designate a monitoring officer**, orders to publicise infringements, administrative fines | Same list, **except no power to designate a monitoring officer** |
| **Escalation if ineffective** | Temporary suspension of certifications/authorisations, or a request to temporarily bar a named CEO/legal representative from managerial duties (subject to procedural safeguards; not applicable to public administration entities) | Not provided for important entities |

**Administrative fines (Article 34) — for infringements of Article 21 (risk management) or Article 23 (reporting)**

- **Essential entities**: maximum of at least **€10,000,000, or at least 2% of total worldwide annual turnover** in the preceding financial year, whichever is higher.
- **Important entities**: maximum of at least **€7,000,000, or at least 1.4% of total worldwide annual turnover** in the preceding financial year, whichever is higher.

These are **EU-wide floors on the national maximum** — Member States must legislate at least this high, and may go higher; the actual fine imposed in any specific case still depends on the severity/duration/damage/intent factors listed in Article 32(7) (which Article 34(3) incorporates by reference). Article 36 is a separate, more general penalties clause covering infringements of national transposing law beyond the specific Article 21/23 violations Article 34 addresses.

**How this compares to CRA and RED penalty structures:** NIS2's figures are lower in absolute euro terms than the CRA's top tier (€15M/2.5%) but apply to a fundamentally different thing — an *organisation's* ongoing risk-management and reporting failures, not a *product's* non-conformity at the point of sale. RED, by contrast, sets no EU-wide figure at all (see [`../red/penalties-enforcement.md`](../red/penalties-enforcement.md)). Do not treat these three penalty regimes as interchangeable or additive without checking which entity/product/obligation triggered which one.

**Jurisdiction (Article 26)**

Entities generally fall under the jurisdiction of the Member State where they are established. Exceptions: providers of public electronic communications networks/services are under the jurisdiction of the Member State where they provide services; DNS providers, TLD registries, domain-registration entities, cloud/data-centre/CDN providers, managed (security) service providers, and online marketplaces/search engines/social-networking providers are under the jurisdiction of the Member State of their **main establishment** in the Union.
