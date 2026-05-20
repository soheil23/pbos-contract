# Example: A PBOS Collaboration in Practice

This is a **fictional** walkthrough of how a company and university lab might set up and run a
PBOS collaboration. All names, data descriptions, and numbers are illustrative. Replace with your
own non-confidential practices.

---

## Scenario

**Acme Marketplace** (a peer-to-peer e-commerce platform) wants to collaborate with **State University**
to study how AI agents can learn to negotiate prices from real transaction logs.
Acme has millions of historical offer/counter-offer sequences; the university has the ML expertise.
The goal: publish a paper and open-source the methodology; Acme retains any trained negotiation model.

---

## Step 1 — Contract setup

The parties use `contracts/PBOS-Template.md` as their starting point.
They fill in the key placeholders:

| Placeholder | Value |
|---|---|
| `[COMPANY]` | Acme Marketplace Inc. |
| `[UNIVERSITY]` | State University |
| `[PROJECT TITLE]` | AI Price Negotiation Research |
| `[YYYY-MM-DD]` | 2025-09-01 |

**"The Science"** is defined as: model architectures, training code, loss functions, evaluation benchmarks,
and any model checkpoint trained exclusively on public or synthetic data.

**Trained Weights** are defined as: any checkpoint produced by training or fine-tuning on Acme's
transaction logs.

The negotiated agreement is kept in Acme's private legal repository — not in this public repo.

---

## Step 2 — Infrastructure setup (Engineering checklist)

- Acme provisions a **restricted cloud project** (e.g., a GCP project or AWS account) with SSO login for the two university researchers.
- Storage buckets containing transaction logs are **read-only** for university accounts and have **no external transfer** permissions.
- A separate **Science export bucket** is created with write access for university researchers; it accepts only files tagged `type=science` in the artifact manifest.
- Access logs are retained for 12 months and are auditable by Acme's security team.

---

## Step 3 — Research workflow

**Phase 1 — Architecture development (pure science, no Company Data)**

The university team designs the negotiation model architecture and writes training code using
**public synthetic data** (randomly generated offer sequences). All checkpoints from this phase
are tagged `base-only` in the manifest and may be freely exported to the public GitHub repo.

**Phase 2 — Training on Acme data (business assets)**

The university team submits training jobs inside the Acme cloud environment.
- Checkpoints produced here are tagged `fine-tuned-on-company-data` and **remain on Acme infrastructure**.
- University researchers have a research license to run evaluation jobs against these checkpoints
  (e.g., compute acceptance rates, revenue metrics) but cannot download the weights.
- Evaluation outputs (aggregate statistics, figures, tables) are reviewed against the Science definition
  before export — they contain no raw transaction data and qualify as The Science.

---

## Step 4 — Nightly artifact manifest

A nightly job runs inside the Acme environment and produces a manifest:

```
filename                        type                      sha256          reviewer
-----------------------------------------------------------------------------------------------
model_arch_v3.py                science                   a1b2c3...       auto
synthetic_pretrain_ckpt.pt      science/base-only         d4e5f6...       auto
acme_finetuned_epoch10.pt       business/trained-weight   —               (stays internal)
eval_results_table1.csv         science                   g7h8i9...       Dr. Smith (Acme)
```

The manifest is signed by Acme's research liaison and archived. The `science` rows are mirrored
nightly to the public GitHub repository.

---

## Step 5 — Publication review

Six months in, the university team drafts a paper. The draft is submitted to Acme's research
liaison **30 days** before the target submission deadline.

Acme's review checklist:
- [ ] No raw transaction data in figures or tables
- [ ] No model weights embedded in the paper
- [ ] Aggregate statistics are not reversible to individual transactions
- [ ] Architecture diagrams describe structure only, not learned parameters

Acme approves the paper with one revision: a figure showing per-category acceptance rates is
replaced with a binned histogram to reduce reconstruction risk. No patent hold is requested.

The paper is submitted. The architecture code, training pipeline, and evaluation benchmarks
are released on GitHub under MIT license — exactly as the contract specified.

---

## Fine-tuning edge case

Midway through the project, a new public base model (e.g., a general-purpose language model)
is released. The team wants to fine-tune it on Acme data instead of training from scratch.

**Classification:**
- The downloaded public checkpoint → **The Science** (base-only; may be listed in the manifest and released).
- The checkpoint after one epoch of fine-tuning on Acme transaction logs → **Trained Weight** (stays in Acme environment, same as any other Acme-trained artifact).

The manifest tagging handles this automatically: the fine-tuned checkpoint inherits the
`business/trained-weight` tag regardless of its starting point.
