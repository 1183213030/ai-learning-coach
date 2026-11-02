# Practice Generation Protocol (引用式练习生成协议)

Specifies the mandatory protocol for generating practice and review items with **traceable source anchoring**, **generator–validator separation**, and **difficulty calibration**. Absorbed in v3.3.0 from DeepTutor (HKUDS, arXiv:2604.26962, §2.3 "Personalized Question Generation") and adapted to the Concept Boundary Contract.

---

## 0. Why This Protocol Exists

A practice item that cannot name its source is an ungrounded probe: it cannot prove coverage, cannot be audited, and silently drifts away from S0 standards. A practice item that is only checked by its own generator risks self-confirming errors (the generator "agrees" with itself). This protocol closes both gaps with two hard requirements:

1. **Every item carries a source anchor** — the learner and the ledger can always walk from item → coverage artifact → S0 claim.
2. **Validation runs in a structurally separate pass** — the validator must not reuse the generator's reasoning chain.

---

## 1. Mandatory Source Anchoring (强制引用)

Every practice item MUST declare a `source_anchor` **before** it is presented to the learner:

```yaml
source_anchor:
  concept_id: "js-closure"            # from knowledge registry
  dimension_id: "d4_reference_identity"  # required dimension in Boundary Coverage Matrix
  artifact_ref: "art-closure-20260930-01"  # coverage artifact that discriminates this boundary
  evidence_ref: null                  # optional: prior evidence.yaml entry (regression checks)
  s0_basis: "Closure retains the lexical environment of its birth scope, by reference, not by copy."
```

Rules:

- **No anchor → no item.** Any generated item lacking a complete, resolvable anchor is rejected as `INVALID_UNGROUNDED_ITEM`.
- **Anchors must discriminate.** The referenced artifact must possess `discriminative_power: strong` (RULE 5 in SKILL.md); a mere topic mention is not an anchor.
- **Anchors must resolve.** `concept_id` must exist in `knowledge/**`; `dimension_id` must exist in `knowledge/dimensions/*.yaml` and be declared `required` or `optional` for that concept.
- **Never invent citations.** If no coverage artifact exists for the target boundary, the item is not yet writable — enqueue teaching/coverage work instead of fabricating an anchor.

---

## 2. Generator–Validator Separation (生成与验证分离)

Practice items are produced in two structurally separate phases:

### Phase A — Generator
Uses the source anchor + learner context (D_w weakness inventory, recent probe performance, spaced interval) to produce the triple `(question, answer, explanation)`.

### Phase B — Validator
An independent pass that **does not reuse the generator's reasoning chain**. It checks, in order:

| Check | Standard |
| :--- | :--- |
| **V1 Template Alignment** | Item modality is one of the review modalities; exactly ONE semantic dimension is being exercised (single-delta rule from SKILL.md §3). Multi-mutation items are `INVALID_CONTROLLED_VARIATION`. |
| **V2 Factual Correctness** | Answer and explanation are correct against the S0 claim. Code items: execute in a sandbox or produce a deterministic step-by-step trace. |
| **V3 Pedagogical Soundness** | Difficulty is calibrated to the learner's current state; the item does not leak the answer (e.g. no spoiler in the question stem); it targets a diagnosed gap rather than a random topic. |
| **V4 Executability** | Any code, snippet, or expected output can actually be run or traced by the coach in this environment. |

- A validator that shares the generator's chain, or that simply "confirms" the generator's output without independent reasoning, is rejected as `INVALID_SELF_VALIDATION`.
- Failed items return **structured diagnostics** (which check failed, what was wrong) and are regenerated at most **2 rounds**; after that, the item is dropped and logged — never presented unvalidated.

---

## 3. Difficulty Calibration (难度校准)

- Difficulty is derived from: **D_w weakness inventory + last probe result + current spaced interval**, not from an arbitrary template list.
- For beginners (L0–L2 teaching budget), one item cluster targets at most **one gap dimension**; never mix a new un-taught dimension into the same item.
- A practice item must be **harder than recognition but easier than unassisted discovery of un-taught material**: it should sit inside the learner's Zone of Proximal Development for the anchored dimension.

---

## 4. Item Schema

```yaml
practice_item:
  id: "pr-20261102-001"
  type: "predict_output"        # one of review-system modalities or mcq
  source_anchor: { ... }        # as in §1
  difficulty: "medium"          # calibrated per §3
  prompt: "..."
  expected: "..."               # correct answer / expected trace
  explanation: "..."            # links back to the S0 claim
  validation:
    status: "passed"            # passed | failed_x2_dropped
    checks: ["V1", "V2", "V3", "V4"]
    validator_note: "..."
  learner_result: null          # filled post-attempt; link into evidence.yaml
```

---

## 5. Audit Trail

- Every **generated** item is logged (session log or a practice log file), regardless of whether it was attempted.
- Every **attempted** item writes its learner result into `evidence.yaml` via the normal Evidence Engine flow, so practice outcomes feed back into D_s and D_r (the closed tutoring loop).
- Regressions found through practice trigger the standard dynamic regression rules in `references/review-system.md`.
