**NIS2 incident reporting (Article 23): the notification clock, and how it differs from CRA Article 14**

**What triggers a notification obligation**

Essential and important entities must notify their national CSIRT (or, where applicable, competent authority) of any **"significant incident"** without undue delay. An incident is significant if (Art. 23(3)):

(a) it has caused, or is capable of causing, severe operational disruption of the entity's services or financial loss for the entity, **or**

(b) it has affected, or is capable of affecting, other natural or legal persons by causing considerable material or non-material damage.

This is a broader trigger than the CRA's Article 14, which is specifically about *actively exploited vulnerabilities* and *severe incidents affecting a product's security*. NIS2's Article 23 covers incidents affecting the entity's own network and information systems and service delivery generally — not specifically a product vulnerability.

**Entities must also, where appropriate, notify affected service recipients** of significant incidents likely to adversely affect service provision, and — separately — communicate to potentially affected recipients any measures they can take in response to a **significant cyber threat** (not yet a realised incident), including informing them of the threat itself where appropriate (Art. 23(1)-(2)).

**Important procedural protection:** "the mere act of notification shall not subject the notifying entity to increased liability" (Art. 23(1)).

**The notification clock (Article 23(4))**

| Stage | Deadline | Content |
| --- | --- | --- |
| **Early warning** | Within **24 hours** of becoming aware of the significant incident | Indicates, where applicable, whether the incident is suspected to be caused by unlawful/malicious acts, or could have cross-border impact |
| **Incident notification** | Within **72 hours** of becoming aware | Updates the early warning; gives an initial assessment including severity, impact, and indicators of compromise where available |
| **Intermediate report** | Upon request from the CSIRT/competent authority | Relevant status updates |
| **Final report** | Not later than **one month** after the incident notification (72h stage) | Detailed description (severity, impact), likely threat/root cause, applied and ongoing mitigation, cross-border impact where applicable |
| **If still ongoing at the final-report deadline** | Progress report at that point, plus a final report within one month of full resolution | — |

**Exception for trust service providers:** significant incidents affecting the provision of trust services must be notified within **24 hours**, without the separate 72-hour intermediate tier used by everyone else.

**How this compares to the CRA's Article 14 clock**

Both regimes use a 24-hour / 72-hour / follow-up structure, and it is easy to conflate them, but they are legally distinct obligations that can apply to different parties for different triggers:

| | **NIS2 Article 23** | **CRA Article 14** |
| --- | --- | --- |
| Who reports | Essential/important **entities** (organisations in Annex I/II sectors) | **Manufacturers** of products with digital elements |
| What triggers it | A "significant incident" affecting the entity's own network/information systems or service delivery | An actively exploited vulnerability, or a severe incident affecting a product's security |
| Early warning | 24 hours | 24 hours |
| Follow-up report | 72 hours (incident notification) | 72 hours |
| Final report | 1 month after the 72h report | 14 days after a fix is available (vulnerability) / 1 month after the 72h report (incident) |
| Applicable from | 18 October 2024 (NIS2 fully applicable) | 11 September 2026 (CRA Art. 14 specifically, ahead of full CRA application) |

A company that both operates NIS2-in-scope infrastructure *and* manufactures CRA-in-scope products could, in principle, owe two separate 24/72-hour notifications to two different bodies for what looks like a related event — one as an "entity" under NIS2, one as a "manufacturer" under the CRA. Don't assume satisfying one automatically satisfies the other.

**Response and information sharing**

The receiving CSIRT/competent authority must respond to the notifying entity, where possible within 24 hours of the early warning, with initial feedback and, on request, guidance or operational advice on mitigation (Art. 23(5)). Where a significant incident affects two or more Member States, the relevant national bodies must inform other affected Member States and ENISA (Art. 23(6)), while preserving the notifying entity's confidentiality and commercial interests. Single points of contact submit quarterly anonymised/aggregated summary reports to ENISA (Art. 23(9)).

**Public disclosure**

Where public awareness is necessary to prevent or respond to a significant incident, or disclosure is otherwise in the public interest, the competent CSIRT/authority may — after consulting the entity — inform the public itself, or require the entity to do so (Art. 23(7)).

**Voluntary reporting (Article 30)**

Separately from the mandatory Article 23 track, Member States must allow voluntary notification — by essential/important entities (for incidents, cyber threats, and near misses) and by *any other entity*, regardless of NIS2 scope, for *significant* incidents, cyber threats and near misses. Voluntary notifications are processed under the same Article 23 procedure, but competent authorities may prioritise mandatory notifications over voluntary ones, and voluntary reporting does not create any additional obligation for the entity that wasn't already there.
