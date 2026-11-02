# Evidence Model & AI Contribution Tracking

This document defines how learning evidence is classified, validated, and logged into `evidence.yaml`. The evidence ledger is the sole ground truth for capability progression.

---

## 1. The Evidence Matrix (E1 to E5)

A capability is not a boolean flag. It is substantiated by five discrete evidence tokens:

| Token | Dimension | Operational Standard | Minimum Passing Threshold |
| :--- | :--- | :--- | :--- |
| **E1: Explain** | Mechanism Verbalization | Learner explains core mechanism in plain language without parrot-repeating AI text. Must identify what problem it solves and what breaks without it. | Accurate cause/effect chain; zero reliance on ungrounded jargon. |
| **E2: Predict** | Mental Runtime Simulation | Learner accurately traces execution order, asynchronous event loop ticks, or state transitions across 2+ steps before execution. | Exact execution order and final state predicted correctly. |
| **E3: Debug** | Error Localization & Repair | Given a broken snippet or stack trace, learner diagnoses root cause, explains why it failed, and implements the fix without AI code dumping. | Root cause correctly identified; fix passes without breaking regressions. |
| **E4: Implement** | Independent Reconstruction | Learner writes the implementation from scratch in a clean file without using AI-generated starter templates or completion. | Functional correctness achieved with `L0` (no hints). |
| **E5: Transfer** | Domain & Context Invariance | Learner recognizes and applies the underlying pattern in an unfamiliar problem space where the technique is not explicitly named. | Pattern recognized and executed under novel constraints. |

---

## 2. AI Contribution Tiers & Mastery Caps

Every learning interaction must evaluate the degree of AI involvement. The AI contribution level sets a hard ceiling on the achievable mastery tier:

```text
+-----------------------+---------------------+-------------------------------+
| AI Contribution Level | Nature of Support   | Maximum Allowable State       |
+-----------------------+---------------------+-------------------------------+
| L5: Full Solution     | AI wrote code/sol   | EXPOSED (0% credit)           |
| L4: Partial Solution  | AI gave skeleton    | GUIDED (Scaffolding only)     |
| L3: Directional Hint  | Strategy suggested  | GUIDED                        |
| L2: Narrowing Hint    | Line/var pointed to | GUIDED                        |
| L1: Open Question     | Socratic question   | GUIDED                        |
| L0: Zero Assistance   | Learner unaided     | INDEPENDENT / TRANSFERABLE    |
+-----------------------+---------------------+-------------------------------+
```

### Strict Prohibition Rules
- **Rule 1**: Copying AI-generated code never yields `E4: Implement` evidence.
- **Rule 2**: Nodding along or responding "yes, I understand" provides 0 evidence points.
- **Rule 3**: Passing a multiple-choice recognition test cannot unlock `INDEPENDENT`.

---

## 3. Evidence Record Schema (`evidence.yaml`)

Every evaluation produces an immutable record in `templates/evidence.yaml`:

```yaml
concept: js-async-await
capability: trace_and_handle_rejections
attempts:
  - id: att-20261001-01
    date: 2026-10-01T14:32:00Z
    task_type: predict_order
    context: "Real project auth interceptor error handling"
    prompt: "Predict which console.log fires first when refreshToken rejects with 401"
    ai_assistance: L0
    learner_response: "catch block runs first, then finally, then caller receives rejected promise"
    result: correct
    confidence_level: high
    evidence_tokens:
      E1_explain: true
      E2_predict: true
      E3_debug: not_tested
      E4_implement: not_tested
      E5_transfer: not_tested
    misconceptions_detected: []
    mastery_state_after: INDEPENDENT
    next_action: "Test E5 Transfer in logging queue tomorrow"
```

---

## 4. Confidence Calibration Tracking

Before grading an attempt, the coach prompts the learner:
> *"How certain are you of this answer? (Low / Medium / High)"*

The coach compares the learner's confidence against actual performance to diagnose meta-cognitive calibration:

- **Correct + High Confidence**: Well-calibrated strength. Advance to higher difficulty or transfer.
- **Correct + Low Confidence**: Under-confident intuition. Reinforce with mechanism validation.
- **Incorrect + Low Confidence**: Aware of knowledge gap. Provide `L2` hint.
- **Incorrect + High Confidence**: **Dangerous Blind Spot**. This represents an active, false mental model. Trigger an immediate counterexample or failure reproduction task.

---

## 5. Trace Forest: Multi-Resolution Memory (轨迹森林多分辨率记忆)

Absorbed in v3.3.0 from DeepTutor (HKUDS) Dynamic Personal Memory (DPM) design (§2.1.2, Trace Forest). The evidence ledger remains the **immutable ground truth for mastery**; the trace forest adds a **retrievable memory layer** so that personalization can cite fine-grained precedents instead of coarse summaries.

### 5.1 Three Levels of Traces

Every tutoring interaction is recorded as a trace tree with three resolutions:

| Level | Granularity | Typical Content |
| :--- | :--- | :--- |
| **L1 Session** | Whole session | Input question, global summary, topics covered, outcome trend |
| **L2 Plan** | Teaching unit | Concept expansion sub-goals, boundary dimensions targeted, teaching strategy used |
| **L3 Execution** | Fine-grained record | Probe prompt, learner response, validation outcome, tool output, misconception flagged |

### 5.2 Trace Record Fields

Appended to `evidence.yaml` entries (or a companion `traces.yaml`) without breaking the ledger's immutability:

```yaml
trace:
  level: "L3"                    # L1 | L2 | L3
  parent_trace_id: "tr-20261007-s3"   # optional; links finer traces to their session/plan
  topic: "js-closure"
  retrieval_keywords: ["private state", "lexical env", "reference identity"]
  summary: "Learner deduced var-loop shares one j by contrast of two loops"
```

### 5.3 Trace Retrieval Budget

When assembling personalized context (per SKILL.md Guardrail 7):

- Retrieve the **most relevant** traces across levels, with budget allocated proportionally (default L1:L2:L3 = 1:2:3, bounded total).
- Role-specific routing: planner/teaching agent consumes L1+L2 summaries; validator consumes L3 execution records; practice generator consumes L3 weaknesses + prior item patterns.

### 5.4 Hard Rules

- **Trace ≠ Mastery.** A trace records observed behavior; mastery state changes ONLY through the Evidence Engine rules (E1–E5, L0–L5 caps, regression transitions).
- **Append-only.** Traces never rewrite prior entries; corrections create new entries with a `supersedes` reference.
- **Evidence-backed weakness only.** Any D_w weakness entry must point to at least one L2/L3 trace or probe record; unanchored weaknesses are `INVALID_UNGROUNDED_CLAIM`.
