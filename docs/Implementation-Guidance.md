# Implementation Guidance (PBOS)

This document translates the PBOS contract into operational steps for legal, engineering, and research teams.

## 1) Device boundary
- Run all data-bearing work on **Company-controlled** systems or cloud accounts.
- Use Company SSO and role-based access for University personnel.

## 2) Export rules
- Permit exports only for **The Science** (code, untrained checkpoints, data-free diagrams, benchmarks not derived from Company Data).
- **Block** export of Trained Weights and raw Company Data.

## 2a) Fine-tuning and multi-stage pipelines
- A public base checkpoint (e.g., downloaded from HuggingFace) is The Science and may be exported freely.
- Once that checkpoint is fine-tuned or continued-pretrained on Company Data, the resulting artifact is a Trained Weight and **must not leave Company infrastructure**.
- In practice: tag each checkpoint with its lineage (`base-only` vs. `fine-tuned-on-company-data`) in the artifact manifest. Treat any checkpoint with Company Data in its training history as a Trained Weight, regardless of how many stages of training have occurred since.

## 3) Artifact manifest & hashing
- Maintain an inventory for each export: filename, size, hash, type (“Science”/“Business”), reviewer sign-off.
- Keep the manifest alongside releases; store the signed copy inside the Company environment.

## 4) Auditability
- Company may review logs and manifests and verify that exported artifacts match “Science” categories.
- Consider periodic third-party reviews for high-sensitivity projects.

## 5) Publication flow
- If a draft contains any Company Confidential Information, send for review **30 days** prior to publication.
- Company may request a limited patent hold (up to **90 days**). Avoid scope creep; this is a safety valve, not a veto.

## 6) Incident response
- Define a single contact channel for reporting security incidents within 24 hours.
- Preserve relevant logs and artifacts until the Company releases the hold.

> These practices align with the core PBOS split: publish the **recipes**; protect the **trained weights**.
