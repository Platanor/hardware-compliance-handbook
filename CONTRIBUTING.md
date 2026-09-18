# Contributing to the Hardware Compliance Knowledge Base

Thanks for wanting to help. This repository only stays useful if it stays accurate — the underlying legislation is still evolving on several fronts (the Cyber Resilience Act's supporting standards under M/606, the EUCC scheme's own implementing act, RED's EN 18031 restrictions, national NIS2 transposition details), so corrections and updates matter more here than in most repos.

## What belongs here

- **Corrections to existing processed guides** — a wrong date, an outdated deadline, a fixed citation, a link that broke. This is the single most valuable kind of contribution.
- **New primary-source mirrors** — official EU texts relevant to CRA, RED, NIS2, or CSA/EUCC (a new delegated/implementing act, a Commission guidance document, an amendment — including the still-missing EUCC scheme implementing act) that aren't in `primary-sources/` yet. Follow the existing provenance-header format (source URL, CELEX identifier, retrieval date, conversion method, coverage caveats, authoritative-version note) — see any existing file in that folder for the template.
- **Flags on stale or provisional content** — several files explicitly note where a standard's status or a deadline is still provisional (e.g. the July 2026 draft amendment to M/606, or EUCC's assurance-level mapping which is not yet independently verified in this repo). If something you flagged as provisional has since been finalized, or vice versa, that's a welcome update.
- **New topic guides**, if there's a relevant subject not yet covered under any of the four regulations — open an issue first to discuss scope before writing one, so the structure stays consistent with the rest of the repo.
- **Additions to `resources/`** — either an independent, third-party framework or playbook genuinely used alongside this legislation (see the three-part test in `resources/index.md`), or a piece of our own analysis that spans more than one regulation and so doesn't fit under a single `cra/`/`red/`/`nis2/`/`csa/` folder. Open an issue first for either kind. If it's our own analysis, it must be marked "Platanor (our own analysis)" in `resources/index.md`'s table, same as the two existing entries — a reader should never have to guess whether a page in that folder is ours or a third party's.
- **Additions to `sbom/`** — same rules as `resources/` (it's the same kind of independent third-party material, just split into its own folder for visibility), scoped specifically to SBOM and VEX. A new worked example belongs in `sbom/examples.md` if it's hand-built for illustration and clearly marked as such; a real, complete example belongs in the format project's own example repository, not here.

## What does NOT belong here

- **Legal advice or definitive compliance conclusions** — no "your product is compliant if X." This repository is explicitly a reference knowledge base, not legal counsel (see the disclaimer in `README.md`). Phrase contributions the same way the rest of the repo does: what the regulation says, not what a reader should conclude about their specific situation.
- **Unverified claims** — every factual statement needs to trace back to a primary source (ideally EUR-Lex or an official EU/ENISA/national-authority publication) or be clearly marked as interpretation rather than fact. If you're not sure a claim is solid, flag the uncertainty in the PR description rather than leaving it implicit.
- **Copyrighted material we can't redistribute** — don't paste in the text of paywalled standards (e.g. EN 18031, IEEE 802.1AR, TCG DICE specifications). Cite them and link to the rights-holder instead, the way `primary-sources/index.md` already does under "What's not here."
- **Vendor or product pitches** — including for Platanor's own services. This repo works because it's a neutral reference; keep it that way.
- **Personal interpretation presented as settled fact** — reasonable people can read an ambiguous provision differently; if you're adding an interpretation, say it's one reading, not the only one.

## How to submit

- **Small fixes** (a date, a broken link, a typo): open a pull request directly.
- **Anything bigger** (a new file, a substantive rewrite, a disputed interpretation): open an issue first so we can agree on scope before you put in the work.
- **New primary-source files**: include the provenance header. A file without one won't be merged, since the whole point of that folder is that every text in it is traceable.
- Cite your source in the PR description — a EUR-Lex link, a CELEX number, an official publication. This is what lets a reviewer (or an LLM reading this repo later) tell "checked" content apart from "someone said so."

## Review

Changes get checked against the primary source before merging, the same way the existing content was fact-checked. If a PR is modified or declined, you'll get the reasoning — the goal is accuracy, not gatekeeping.

## Language

The repository is maintained in English. If you want to contribute a translation into another language, open an issue first — we're open to it, but it needs a clear structure (e.g. a parallel directory) so it doesn't fragment the single source of truth.
