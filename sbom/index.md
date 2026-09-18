# SBOM and VEX — software bill of materials and vulnerability exploitability

CRA Annex I, Part II, point 1 requires manufacturers to identify and document the product's components, "including by drawing up a software bill of materials in a commonly used and machine-readable format covering at the very least the top-level dependencies of the products" (see [`../cra/essential-requirements.md`](../cra/essential-requirements.md)). That single sentence is the reason this folder exists: it's one specific, named obligation in the regulation, not a general best practice, and it's usually the first concrete engineering question a manufacturer asks once they've read the CRA overview.

This folder covers what that obligation actually means in practice: the two formats a manufacturer's SBOM tooling will actually produce, the companion VEX mechanism for saying whether a listed vulnerability actually matters for this product, and worked examples of both formats side by side so the shape of an actual file is visible, not just described.

## Contents

| File | What it is |
| --- | --- |
| [formats-and-specifications.md](formats-and-specifications.md) | CycloneDX and SPDX formats, SWID tags, and the 2026 CISA minimum elements for SBOM content |
| [vex.md](vex.md) | VEX — documenting whether a vulnerability in the SBOM actually affects the product; three specifications (CycloneDX VEX, CSAF VEX, OpenVEX) |
| [examples.md](examples.md) | A worked example SBOM for the same hypothetical device, written out in both CycloneDX and SPDX, plus a CycloneDX example with an embedded VEX statement |

## Why a dedicated folder

SBOM and VEX used to live inside `resources/`, alongside independent frameworks like PSA Certified and the ENISA Secure by Design and Default Playbook. They still fit that folder's definition — CycloneDX, SPDX, and the VEX implementations are all independently governed, third-party specifications, not our own analysis — but SBOM specifically is tied to a single, precisely quoted line in CRA Annex I, and it's the most commonly asked-about topic in this repository. Burying it three links deep inside a folder named for a different purpose made it easy to miss. Pulling it into its own top-level folder doesn't change what it is (still a third-party specification, summarized and linked out, not reproduced), only how easy it is to find.

## Sourcing

Same rule as `resources/`: CycloneDX, SPDX, and all three VEX implementations remain independently governed, trademarked specifications (OWASP Foundation and Ecma International for CycloneDX and CycloneDX VEX, the Linux Foundation for SPDX, OASIS Open for CSAF VEX, OpenSSF for OpenVEX). The pages in this folder summarize and illustrate them — including the worked examples in `examples.md`, which are hand-built for illustration and checked against the official JSON schemas, not pulled from a real product — they are not a substitute for the official specifications and example repositories linked from each page.

See [`../CONTRIBUTING.md`](../CONTRIBUTING.md) for the general contribution process; additions here follow the same third-party sourcing rules as `resources/`.
