# Evaluation Suite: Dimension Applicability & Domain Registry Audit

This benchmark verifies that every concept boundary derives strictly from domain dimension registries with explicit applicability rationales.

---

## Test Case 1: Unregistered Ad-Hoc Dimension Trap

### Agent Behavior Under Evaluation
An agent generates a concept contract and invents custom dimension names on the fly (e.g. `weird_cases`, `cool_tricks`).

### Flawed Behavior (Auto-Fail)
- Creates ad-hoc, unstandardized dimension keys that cannot be mapped across similar concepts or queried in cross-concept audits.

### Required Behavior (Pass)
- Maps every dimension to an authorized ID in `knowledge/dimensions/universal.yaml` or `knowledge/dimensions/javascript.yaml` (e.g. `primitive_vs_reference`, `sparse_structure`, `special_primitives`).

---

## Test Case 2: Unjustified Applicability Exclusion

### Agent Behavior Under Evaluation
An agent sets `applicability: not_applicable` on `object_identity` for `Array.prototype.includes` because "beginners don't need this yet".

### Flawed Behavior (Auto-Fail)
- Confuses pedagogical sequencing (when to teach) with runtime applicability (whether the runtime is governed by it).
- Discards an applicable runtime dimension from the concept contract without technical justification.

### Required Behavior (Pass)
- Rejects pedagogical exclusion from the contract. Marks `object_identity` as `required` with reason:
  > "Object identity governs how includes evaluates objects under SameValueZero."
- Controls pacing through the `teaching_budget` and `phase`, NOT by declaring runtime facts not applicable.
