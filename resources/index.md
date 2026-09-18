# Resources — independent frameworks, tools, and our own cross-cutting analysis

SBOM and VEX formats used to live in this folder and now have their own dedicated [`../sbom/`](../sbom/index.md) folder — pulled out because SBOM is tied to a specific, named line in CRA Annex I and was the single most commonly asked-about topic buried in here. See [`../sbom/index.md`](../sbom/index.md) for CycloneDX, SPDX, VEX, and worked examples of both formats.

Unlike `primary-sources/` (raw official EU legal text) and `cra/`, `red/`, `nis2/`, `csa/` (our own fact-checked analysis organised by a single regulation), this folder holds two related but distinct kinds of material:

1. **Independent, third-party material** — frameworks, certification schemes, and practical playbooks that are not part of EU law but are commonly used alongside it to turn a legal requirement into a concrete engineering decision. Nothing in this category is legally required by the CRA, RED, NIS2, or CSA; where one of these is genuinely useful for a specific requirement, that connection is stated explicitly in the file — treat it as a practical cross-check, not as a compliance shortcut.
2. **Our own cross-cutting analysis** — write-ups that are Platanor's own fact-checked work (same status as `cra/`, `red/`, `nis2/`, `csa/`), just organised by *task* rather than by regulation because they span more than one regulation at once (e.g. how the CRA relates to other EU law, or CE marking that requires both CRA and RED). These carry no independent publisher — they're ours, CC BY 4.0 like the rest of the repository — and each is marked as such in the table below so it isn't mistaken for a third-party source.

## Contents

| File | What it is | Publisher | License / access |
| --- | --- | --- | --- |
| [psa-certified.md](psa-certified.md) | IoT hardware security framework + independent lab certification (Root of Trust, 4 levels) | GlobalPlatform | Independent scheme; certification is a paid, lab-evaluated process — we link out, no reproduction |
| [enisa-secure-by-design-default-playbook.md](enisa-secure-by-design-default-playbook.md) | 22 practical Secure by Design / Secure by Default checklists for SME engineering teams | ENISA | CC BY 4.0 — free, we hold an internal mirror, this page links to the canonical GitHub source |
| [relationship-to-other-eu-law.md](relationship-to-other-eu-law.md) | How the CRA relates to NIS2, RED, the AI Act, the Machinery Regulation, MDR, automotive rules, GDPR, and the CSA/EUCC | **Platanor (our own analysis)** | CC BY 4.0, same as the rest of this repository |
| [cra-red-ce-marking-guide.md](cra-red-ce-marking-guide.md) | Practical step-by-step guide to CE marking for a connected device, walking through both CRA and RED at once | **Platanor (our own analysis)** | CC BY 4.0, same as the rest of this repository |

## Why a separate folder

`cra/essential-requirements.md` and `red/essential-requirements.md` already reference the third-party frameworks above in passing, at the specific points where they're relevant. This folder gives each one a full standalone page — what it actually is, how it's structured, and exactly which requirement it does (and doesn't) help with — instead of a bare link inside a paragraph about something else. The two cross-cutting guides live here for a related but separate reason: they don't belong to any single regulation's folder, since walking through CE marking or explaining how the CRA interacts with other law necessarily spans `cra/`, `red/`, `nis2/`, and `csa/` at once.

## Adding to this folder

A **third-party resource** belongs here if it meets all three: (1) it is independently published, not our own analysis; (2) it is genuinely used in practice for CRA/RED/NIS2/CSA-adjacent engineering decisions, not just tangentially related; (3) we can state a specific, defensible connection to a named requirement rather than a vague "this is good for security" claim.

A piece of **our own cross-cutting analysis** belongs here instead of in a single regulation's folder if it genuinely can't be organised under just one of `cra/`, `red/`, `nis2/`, `csa/` without an arbitrary choice — and it must be marked "Platanor (our own analysis)" in the table above, exactly like the two entries here, so a reader never has to guess whether a page in this folder is ours or a third party's.

See [`CONTRIBUTING.md`](../CONTRIBUTING.md) for the general contribution process.
