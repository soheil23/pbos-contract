# PBOS: Protect-the-Business / Open-Source-the-Science

> **Version: v0.1.0** — See [CHANGELOG.md](CHANGELOG.md) for version history.

A small, **generic** template and playbook for setting up academia–industry ML collaborations where
company data must remain protected while scientific artifacts remain open.

This repo provides:
- A minimal **PBOS Contract Template** (Markdown) with placeholders (`[COMPANY]`, `[UNIVERSITY]`, etc.).
- **Implementation guidance** covering device boundaries, export rules, fine-tuning pipelines, and auditability.
- A short **clause pack** you can paste into existing agreements.
- Checklists for counsel, researchers, and engineering teams.

> **Disclaimer**: This is not legal advice. Use at your own risk. Adapt with counsel.
> Keep confidential information out of this repository and your pull requests.

## Paper

PBOS is introduced and motivated in:

> Dirk Bergemann, Soheil Ghili, Nitzan Mekel-Bobrov.
> **”Position: The Pre/Post-Training Boundary Should Govern IP in Industry–Academia ML Collaborations.”**
> Working Paper, May 2026. \[[link](https://sites.google.com/view/soheil-ghili/pbos)\]

If you use PBOS as a starting point, please cite the paper.

## Who this is for
- Data-rich companies that want to collaborate with academic labs without losing control of trained models.
- Universities that need to publish architectures, code, and benchmarks as part of academic careers.
- Technology transfer offices looking for a standard starting template for ML research agreements.

## Core idea (one sentence)
**Publish the recipes; keep the secret sauce.** Untrained models, architectures, and code are “the science.”
Any model trained on proprietary data is “the business” and stays with the company.

This boundary also handles fine-tuning: a publicly available base checkpoint is The Science; the same
checkpoint after fine-tuning on Company Data becomes a Trained Weight and belongs to the company.
The criterion is not the origin of the weights but their exposure to proprietary data.

## Repo structure
```
contracts/           # PBOS-Template.md (full agreement), Clause-Pack.md (drop-in clauses)
docs/                # Implementation-Guidance.md, Checklists.md
examples/            # Fictional walkthrough of a PBOS collaboration
.github/ISSUE_TEMPLATE/
CONTRIBUTING.md      # How to propose improvements
CHANGELOG.md         # Version history
```

## Quick start
1. Copy `contracts/PBOS-Template.md` into your private legal repo.
2. Search-and-replace placeholders (`[COMPANY]`, `[UNIVERSITY]`, `[PROJECT TITLE]`, etc.).
3. Run through `docs/Checklists.md` with counsel + tech leads.
4. Keep your negotiated contract **private**; share improvements here as generic language suggestions via the [Language Proposal](.github/ISSUE_TEMPLATE/language-proposal.yml) issue template.

## Contributing
See [CONTRIBUTING.md](CONTRIBUTING.md).

## License
- Text in this repo: CC BY 4.0 (see `LICENSE`).
- No code is provided; if you add code samples, consider Apache-2.0.
