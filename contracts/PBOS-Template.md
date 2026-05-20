# PBOS Collaboration Template (Generic)

> **Purpose**: Provide a minimal structure that lets a company and a university
> collaborate while maintaining a clear boundary between publishable science and
> proprietary business assets.

**Parties**: `[COMPANY]` (the “Company”) and `[UNIVERSITY]` (the “University”).  
**Project**: `[PROJECT TITLE]`.  
**Effective Date**: `[YYYY-MM-DD]`.

---

## 1. Definitions

- **Company Data**: Any data, code, logs, or materials the Company provides for the Project.
- **The Science**: Mathematical descriptions, model architectures, algorithmic methods, computer programs,
  and data-free visual exhibits that describe how the system works **without** incorporating or depending on
  Company Data. *Examples*: untrained model checkpoints; code; diagrams; derivations; benchmarks not derived
  from Company Data.
- **Trained Weights**: Any model parameters obtained by training/fine-tuning on Company Data.
- **Work Product**: Any outputs created in the Project, including models, reports, code, and analyses.

> **Key boundary rule**: An **untrained** model (or a model trained only on public or synthetic data) is **The Science**.
> A model **trained on Company Data** is **Trained Weights** and part of the Company’s business assets.
> (This is the heart of PBOS.)
>
> **Fine-tuning and transfer learning**: A publicly available base checkpoint is The Science. That same
> checkpoint after fine-tuning or continued pre-training on Company Data becomes Trained Weights and belongs
> to the Company. The criterion is **exposure to Company Data**, not the origin of the starting weights.
> This applies to all multi-stage pipelines: each stage that touches Company Data produces a Trained Weight.

## 2. Scope & Permitted Use

University may access Company Data **solely** to conduct the Project as defined in Exhibit A (if any).
No other use is permitted without written consent from the Company.

## 3. Ownership & Licenses

1. **Company Materials and Trained Weights**: Company owns Company Data and all Trained Weights and any
   Work Product that incorporates Company Data. University receives a **research-only** license to use Trained Weights
   for replication and academic evaluation; **no commercial use**.
2. **The Science (University Work Product)**: University owns The Science and may **publish** it under a permissive
   open-source license (e.g., MIT/Apache-2.0) and in academic venues. Company receives a **non-exclusive, royalty-free,
   worldwide license** to use The Science internally and commercially.
3. **Joint Work Product**: Outputs created jointly without Company Data are jointly owned; parties may exploit
   them unless agreed otherwise in writing.

## 4. Publication & Review

University may publish **The Science**. If a draft contains Company Confidential Information, it must be submitted
to Company **30 days** before public disclosure for security/privacy review and optional patent filing holds (up to 90 days).

## 5. Operational Safeguards (Security & Audit)

- All processing of Company Data occurs on **Company-controlled systems** (or Company-managed cloud).
- **Exports** from those systems are limited to **The Science** (no Trained Weights or raw Company Data).
- Company may **audit** compliance (e.g., access logs; artifact inventories). The parties may use cryptographic hashes
  and artifact manifests to prove that exported files are limited to The Science.
- University will promptly report suspected security incidents as specified in an attached security addendum.

## 6. Confidentiality

Terms of the Agreement and Company Data are confidential. Exceptions: information already public, independently
developed without reference to confidential information, or required by law to be disclosed (with notice).

## 7. Term & Termination

Either party may terminate on 30 days’ notice. Upon termination, University will cease use of Company Data and
destroy or return all copies on third-party systems, keeping only The Science and records needed for compliance.

## 8. Dispute Resolution

Disputes first go to good-faith negotiation between the Company’s project lead and the University PI.
If unresolved within 30 days, escalate to counsels or a mutually agreed mediator.

## 9. Exhibit A (Optional): Project Summary

- **Purpose**: `[short description]`  
- **Company Materials needed**: `[fields/data types]`  
- **Expected outputs**: e.g., algorithms, evaluation benchmarks, paper(s), untrained checkpoints  
- **Timeline**: `[e.g., 3–6 months]`

---

> **Notes for implementers**
> - Keep this template **generic** and free of confidential specifics.
> - Replace placeholders and move the finalized agreement to your private legal repository.
> - Use `docs/Checklists.md` to operationalize.
