**ENISA Secure by Design and Default Playbook — 22 practical checklists for SMEs**

**What it is**

On 30 July 2026, ENISA published an official *Secure by Design and Default Playbook: A Practical Guide to Secure by Design and Default for SMEs*, distributed as a GitHub repository under CC BY 4.0: [github.com/enisaeu/enisa-sbd-playbook](https://github.com/enisaeu/enisa-sbd-playbook) (source PDF: [ENISA publication page](https://www.enisa.europa.eu/publications/enisa-secure-by-design-and-default-playbook)). It is non-legal guidance — ENISA's own stated goal is to bridge the gap between the aspirational "secure by design" principle and concrete, checklist-level implementation within the constraints of a small engineering team.

**Structure: 22 playbooks in two groups**

| Secure by Design — Architectural Foundations | Secure by Design — Operational Integrity |
| --- | --- |
| 01 Trust boundaries and threat modelling | 07 Life-cycle management |
| 02 Least privilege | 08 User-centric design |
| 03 Strong identity and authentication architecture | 09 Secure coding and verification practices |
| 04 Attack surface minimisation | 10 Logging, monitoring and alerting |
| 05 Defence in depth | 11 Configuration and change management |
| 06 Open design | 12 Incident response and recovery |
| | 13 Vulnerability and patch management |
| | 14 Supply-chain controls |

| Secure by Default — Default Hardening | Secure by Default — Guided Protection |
| --- | --- |
| 15 Minimisation of default services | 19 Mandatory security onboarding |
| 16 Restrictive initial access | 20 Automated maintenance and updates |
| 17 Secure communication by default | 21 Transparent security posture |
| 18 Unique device identity and secrets by default | 22 Secure recovery and ownership life cycle |

Every individual playbook follows the same five-part template: **Principle → Objective → Checklist → Minimum evidence → Release gate.** The "minimum evidence" and "release gate" fields are the practically useful part — they turn an abstract principle into a concrete, auditable artefact a team can point to at release time.

**Progressive adoption**

ENISA explicitly does not expect all 22 to be implemented at once. It suggests three stages: (1) establish context and priorities via threat modelling (playbook 01), (2) build a foundational engineering baseline (secure coding, logging, patch management, supply-chain controls, unique device identity, secure communication, automated updates — playbooks 09, 10, 13, 14, 16, 17, 18, 20), then (3) broaden coverage to the remaining playbooks based on product-specific risk. ENISA is explicit that this sequencing is illustrative, not a reason to defer any requirement that is already a legal obligation — including CRA obligations, which take precedence regardless of where a playbook sits in the suggested order.

**Intended audience** (as stated by ENISA): software developers and engineers, technical product managers, SME security leads, and system architects — explicitly "particularly relevant to SME manufacturers developing products with digital elements."

**Why it's listed here**

The playbook does not name specific CRA Annex I sub-points inside the principle text itself — the mapping between playbooks and Annex I points lives only in the source document's own Annex C, not duplicated here. Use it as a second, EU-official cross-check when auditing a product's architecture: work through the 22 principles independently of the Annex I table in [`cra/essential-requirements.md`](../cra/essential-requirements.md), then confirm that any gap found also shows up against the matching point in that table. Playbooks 13 (Vulnerability and patch management) and 14 (Supply-chain controls) are the closest in scope to this repository's Annex I Part II material (SBOM, vulnerability handling, CVD).

**Provenance of our mirror:** this repository also holds a full markdown mirror of the 22 playbooks internally (commit `6ec97bec2b5b58e84edfec9f1695ddda9008ace0`, mirrored 30 July 2026, CC BY 4.0, attribution: ENISA) for searchable/diffable internal reference. This page links to the canonical GitHub source rather than republishing all 22 files, to avoid drifting out of sync if ENISA updates them.
