# Contributing to PBOS

Thanks for your interest in improving PBOS. The goal is to make this template more useful and
robust for real collaborations — contributions that reflect hard-won negotiating experience are
especially welcome.

## Ground rules

1. **Keep everything generic.** No company names, institution-specific terms, or confidential
   language. Use placeholders like `[COMPANY]` and `[UNIVERSITY]`.
2. **This is not legal advice.** Don't present contributed language as legally authoritative.
   Contributors and maintainers are not acting as counsel.
3. **No confidential information in issues or PRs.** If your contribution was inspired by a
   real negotiation, strip it down to the generic principle before posting.

## How to contribute

### Propose a clause or template improvement
Use the [Language Proposal](.github/ISSUE_TEMPLATE/language-proposal.yml) issue template.
Describe the problem the clause addresses and provide generic suggested language.
Maintainers will review and integrate well-reasoned proposals into the template or clause pack.

### Submit an example or walkthrough
Add a file to `examples/` following the style of `examples/Example-Integration-Notes.md`:
a fictional but realistic scenario that shows how PBOS works in practice. Open a PR with
a brief description of what the example adds.

### Fix a gap in the implementation guidance
If you've run into an edge case not covered in `docs/Implementation-Guidance.md` (e.g., a
novel pipeline architecture, a jurisdiction-specific auditability requirement), open an issue
or PR describing the gap and a proposed solution.

### Report an inconsistency
If you find language in `contracts/PBOS-Template.md` that contradicts `docs/` or the
[paper](https://github.com/soheil23/pbos-contract), open an issue describing the conflict.

## What we are not looking for

- Jurisdiction-specific legal terms that don't generalize.
- Contributions that weaken the core PBOS boundary (the pre/post-training distinction).
- Fully negotiated contracts — keep those in your private legal repository.

## Versioning

PBOS follows [Semantic Versioning](https://semver.org/):
- **Patch** (v0.1.x): typo fixes, clarifications that don't change meaning.
- **Minor** (v0.x.0): new clauses, new examples, or guidance that extends coverage without
  breaking existing language.
- **Major** (vx.0.0): changes to the core boundary definition or ownership structure.

Update `CHANGELOG.md` in any PR that changes versioned content.
