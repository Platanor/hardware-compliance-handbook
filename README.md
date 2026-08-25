# Hardware Compliance Knowledge Base

**A fact-checked, open reference on the EU laws that govern hardware and IoT cybersecurity — CRA, RED, NIS2, and the Cybersecurity Act/EUCC, in one place instead of four.**

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/) [![Regulations covered](https://img.shields.io/badge/regulations-CRA%20%7C%20RED%20%7C%20NIS2%20%7C%20CSA%2FEUCC-blue)](#repository-structure) [![Maintained by](https://img.shields.io/badge/maintained%20by-Platanor%20Technologies-2f855a)](https://platanor.com)

Prepared by **Platanor Technologies** ([platanor.com](https://platanor.com)) — an embedded security firm for IoT device manufacturers.

**Contents:** [Quick start](#quick-start) · [What this is](#what-this-is) · [Repository structure](#repository-structure) · [Methodology](#methodology-and-sourcing) · [Using with an LLM](#how-to-use-this-with-an-llm) · [Claude Skill](#installing-this-as-a-claude-skill) · [Feedback](#feedback) · [License](#license) · [Discussions](https://github.com/Platanor/hardware-compliance-handbook/discussions)

---

## Quick start

- **Just want an answer?** Open [`cra/faq.md`](cra/faq.md), [`red/faq.md`](red/faq.md), [`nis2/faq.md`](nis2/faq.md), or [`csa/faq.md`](csa/faq.md) — each is a practical Q&A for hardware/IoT manufacturers, no legal background required.
- **Working with an LLM?** Drop a processed guide into your prompt and ask, e.g.: *"Using `cra/product-risk-classes.md` and `red/essential-requirements.md`, does a Wi-Fi-connected baby monitor need a notified body, or can we self-assess?"*
- **Need the exact legal wording?** Every processed guide links back to its source in [`primary-sources/`](primary-sources/) — full official text, chunked by article.
- **Want this loaded automatically in Claude?** See [Installing this as a Claude Skill](#installing-this-as-a-claude-skill).

---

## ⚠️ Disclaimer — read before use

**This is NOT legal advice.** The materials in this repository are a reference knowledge base on the main pieces of EU law that touch hardware and IoT cybersecurity — the **Cyber Resilience Act** (Regulation (EU) 2024/2847), the **Radio Equipment Directive** (Directive 2014/53/EU and its cybersecurity delegated act), the **NIS2 Directive** (Directive (EU) 2022/2555), and the **Cybersecurity Act** (Regulation (EU) 2019/881, including the EUCC certification framework) — prepared to help you orient yourself in the topic, not to inform legal or compliance decisions.

- We make an effort to keep facts accurate and checked against the primary text of each regulation (EUR-Lex), but **we give no guarantee of completeness or currency** — this legislation and its supporting standards (M/606, harmonised standards, delegated/implementing acts) are still under development and can change.
- Before making any decision about your product's or organisation's compliance — **consult a qualified lawyer or regulatory advisor** who can assess your specific case.
- This is a **living, growing knowledge base**: materials are regularly expanded, corrected, and re-verified. What is accurate today may have changed in a deadline or an interpretation — always check a file's last-verified date against the current state of the regulation.
- Found an error or inaccuracy? We'd appreciate the feedback (see "Feedback" below).

---

## What this is

Hardware and IoT manufacturers selling into the EU are increasingly subject to more than one regulation at once — the CRA governs the *product*, RED governs *radio equipment* specifically (with its own overlapping cybersecurity requirements), NIS2 governs certain *organisations* in critical sectors (including some manufacturers and their customers), and the Cybersecurity Act provides the *voluntary certification framework* (EUCC) that sits alongside all of them. This repository exists because treating any one of these in isolation gives an incomplete picture — a manufacturer can be in full CRA compliance and still miss a RED-specific requirement, or misjudge whether NIS2 reaches them indirectly through a customer's supply-chain obligations.

The repository has two layers:

1. **Processed guides** (`cra/`, `red/`, `nis2/`, `csa/`) — shorter, structured reference documents per regulation: overview, definitions/scope, essential requirements or obligations, deadlines, penalties, and a practical FAQ. Easy to use for a quick grasp of a topic, and each one is written to flag how it relates to the other three regulations, not just to stand alone.
2. **Primary sources** (`primary-sources/`) — the full official text of each regulation and related act, unmodified. The source of truth for exact quotes, for humans and LLMs alike.

The processed guides have been fact-checked against the primary text of each regulation and related sources (M/606, delegated/implementing acts) — methodology described below.

## Repository structure

### CRA — Cyber Resilience Act (Regulation (EU) 2024/2847)

| File | What it covers |
|---|---|
| [`cra/overview.md`](cra/overview.md) | Adoption context, scope, structure of the regulation (chapters and annexes) |
| [`cra/definitions.md`](cra/definitions.md) | Official definitions and terminology (product with digital elements, RDPS, critical/important product, etc.) |
| [`cra/essential-requirements.md`](cra/essential-requirements.md) | Annex I essential cybersecurity requirements + status of harmonised standards development (mandate M/606); cross-referenced against ENISA's Secure by Design and Default Playbook |
| [`cra/product-risk-classes.md`](cra/product-risk-classes.md) | Product risk classification: Default, Important Class I/II, Critical |
| [`cra/obligations-by-role.md`](cra/obligations-by-role.md) | Manufacturer, importer, and distributor obligations (Chapter II) |
| [`cra/timeline-deadlines.md`](cra/timeline-deadlines.md) | Key deadlines and transitional provisions |
| [`cra/vulnerability-reporting.md`](cra/vulnerability-reporting.md) | Vulnerability and severe-incident reporting (Article 14) |
| [`cra/penalties-enforcement.md`](cra/penalties-enforcement.md) | Penalties and market surveillance |
| [`cra/self-assessment-maturity-model.md`](cra/self-assessment-maturity-model.md) | ENISA SME Cyber Resilience Maturity Assessment Model |
| [`cra/faq.md`](cra/faq.md) | Practical FAQ for hardware/IoT manufacturers |

### RED — Radio Equipment Directive (2014/53/EU + cybersecurity delegated act)

| File | What it covers |
|---|---|
| [`red/overview.md`](red/overview.md) | Scope, structure, relationship to the CRA |
| [`red/essential-requirements.md`](red/essential-requirements.md) | Art. 3(3)(d)(e)(f) cybersecurity requirements, EN 18031-1/-2/-3 and their restrictions |
| [`red/obligations-by-role.md`](red/obligations-by-role.md) | Manufacturer, importer, and distributor obligations (Chapter II) |
| [`red/timeline-deadlines.md`](red/timeline-deadlines.md) | Key deadlines: the directive, the cybersecurity delegated act, harmonised standards |
| [`red/penalties-enforcement.md`](red/penalties-enforcement.md) | Penalties (set by national law, not EU-wide) and market surveillance |
| [`red/faq.md`](red/faq.md) | Practical FAQ for hardware/IoT manufacturers |

### NIS2 — Directive (EU) 2022/2555

| File | What it covers |
|---|---|
| [`nis2/overview.md`](nis2/overview.md) | Scope, essential/important entity split, structure |
| [`nis2/obligations.md`](nis2/obligations.md) | Governance (Art. 20), risk-management measures (Art. 21), essential vs. important supervision (Art. 32/33), fines (Art. 34) |
| [`nis2/incident-reporting.md`](nis2/incident-reporting.md) | Reporting obligations (Art. 23) — notification clock, comparison with CRA Art. 14 |
| [`nis2/faq.md`](nis2/faq.md) | Practical FAQ for hardware/IoT manufacturers and their customers |

### CSA — Cybersecurity Act / EUCC (Regulation (EU) 2019/881)

| File | What it covers |
|---|---|
| [`csa/overview.md`](csa/overview.md) | ENISA mandate + the European cybersecurity certification framework, relationship to CRA/RED/NIS2 |
| [`csa/eucc-certification.md`](csa/eucc-certification.md) | EUCC certification mechanics — assurance levels, voluntary status, issuing bodies |
| [`csa/faq.md`](csa/faq.md) | Practical FAQ on CSA/EUCC for hardware/IoT manufacturers |

### Cross-cutting and primary sources

| File | What it covers |
|---|---|
| [`relationship-to-other-eu-law.md`](relationship-to-other-eu-law.md) | How the CRA interacts with other EU law: RED, NIS2, AI Act, CSA/EUCC, GDPR, and others |
| [`cra-red-ce-marking-guide.md`](cra-red-ce-marking-guide.md) | Practical step-by-step guide to CE marking under both CRA and RED |
| [`primary-sources/`](primary-sources/index.md) | Full official text of the CRA, M/606, RED, NIS2, CSA, and related acts |

## Methodology and sourcing

Every statement is checked against a source-priority order: **primary text of the regulation (EUR-Lex) > official related documents (standardisation mandates, delegated/implementing acts) > secondary sources > our own analysis**. Where there is an open question or a not-yet-finalised rule (e.g. the draft amendment to M/606), this is explicitly flagged in the text as pending official confirmation, not stated as settled fact.

## How to use this with an LLM

These files are designed to serve as context for language models (ChatGPT, Claude, Gemini, etc.) — for example:

- attach the relevant `.md` file (or several) as context to your prompt when asking a model about CRA, RED, NIS2 or CSA/EUCC — the processed guides are enough for a quick answer; for an exact article quote, use a file from `primary-sources/`;
- use the repository as a source for a RAG pipeline or your own hardware-compliance assistant — the primary-source files in `primary-sources/` are already split by `### Article N` headings, which are natural chunking boundaries;
- the markdown format has no complex layout — easy to parse and chunk;
- the repository root has an [`llms.txt`](llms.txt) — a concise, machine-readable index of all files for AI agents.

Since a model's answers will be grounded in these files, the disclaimer above applies to any LLM output built on this base too — those answers are likewise not legal advice.

## Installing this as a Claude Skill

This repository has a [`SKILL.md`](SKILL.md) file at its root, alongside the reference files — so it can be installed as a [Claude Skill](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview): a packaged capability that Claude loads automatically whenever a question matches its topic, instead of you having to attach files by hand every time. Installation differs by product, since Skills don't sync across surfaces:

**Claude Code** (filesystem-based, no upload step):
```bash
git clone https://github.com/Platanor/hardware-compliance-handbook.git ~/.claude/skills/hardware-compliance-handbook
```
Use `~/.claude/skills/` for a personal install available in every project, or clone into a project's own `.claude/skills/` folder to scope it to that project. Claude Code discovers `SKILL.md` automatically — no restart or extra config needed.

**claude.ai, Claude Desktop, or Cowork:**
1. Clone or download this repository, then zip its contents (e.g. `zip -r hardware-compliance-knowledge-base.zip .` run from inside the repo folder).
2. In your Claude settings, go to **Settings → Features → Skills** (requires a Pro, Max, Team, or Enterprise plan with code execution enabled) and upload the zip file.

Skills uploaded this way are tied to your individual account — each teammate who wants it needs to upload it separately.

**Claude API / your own application:** upload the repository as a Custom Skill through the Skills API (`/v1/skills`). See Anthropic's [Agent Skills documentation](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) for the full reference.

However you install it, this remains a knowledge base, not a certified compliance tool — the disclaimer at the top of this README applies to anything Claude produces using it.

## Status

Actively growing. Currently 25 processed documents across four regulations (CRA, RED, NIS2, CSA/EUCC) plus 8 primary-source mirrors; more material is planned as the underlying legislation develops (new harmonised standards, delegated/implementing acts, Commission guidance, and the still-unmirrored EUCC scheme implementing act).

## Feedback

Found an error, an outdated date, or an inaccurate interpretation? Let us know — contact details at [platanor.com](https://platanor.com), or open an issue or pull request directly. See [`CONTRIBUTING.md`](CONTRIBUTING.md) for what belongs here and how to submit a change.

Have a question, a use case to share, or want to suggest what should be covered next? Use [GitHub Discussions](https://github.com/Platanor/hardware-compliance-handbook/discussions) — issues/PRs are for content fixes, Discussions is for everything else.

## License

This content is distributed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license.

This means you're free to copy, redistribute, adapt, and even use these materials commercially — provided you give attribution: credit **Platanor Technologies** ([platanor.com](https://platanor.com)) as the source and link to the license.

Full license text: [creativecommons.org/licenses/by/4.0](https://creativecommons.org/licenses/by/4.0/). Details in the [`LICENSE`](./LICENSE) file.

---

If this saved you from reading four EU regulations back to back, a ⭐ on the repo helps other manufacturers find it too.
