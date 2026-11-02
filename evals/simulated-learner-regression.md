# Simulated-Learner Regression Testing (模拟学习者回归测试)

Defines the protocol-level regression test that verifies the coach **adapts to a specified learner** rather than merely following the syllabus. Absorbed in v3.3.0 from DeepTutor's TutorBench (HKUDS, arXiv:2604.26962, §4) first-person interactive evaluation protocol, adapted to the coach's Concept Boundary Contract.

---

## 1. When to Run

- **After any protocol upgrade** — SKILL.md, references/, templates/, or evals/ changed.
- **When a new concept** enters `knowledge/` registry (verifies the new concept's boundary contract is teachable, not just documented).
- **When `REGRESSION DETECTED`** or systematic probe failures appear in real sessions (verifies the protocol, not just the learner).

---

## 2. Simulated Learner Specification

Each test run specifies one simulated learner (mirroring TutorBench's profile + gap + task triple):

```yaml
simulated_learner:
  profile:
    baseline: "beginner"            # beginner | intermediate | advanced
    target_role: "前端求职"          # goal drives personalization
    style: "concrete_first"
  grounded_weaknesses:              # 1-3, each anchored to a real concept + manifestation
    - concept_id: "js-closure"
      manifestation: "Believes outer variable is copied by value into inner function"
      correct_understanding: "Closure retains the lexical environment by reference"  # reserved for judging
  task: "Ask the tutor to explain closure and then generate a review item targeting the misconception"
  source_anchor: "js-closure d4_reference_identity"  # must resolve in knowledge registry
```

Rules: the manifestated weakness and correct understanding are both written BEFORE the run; the correct understanding is **never exposed to the coach**.

---

## 3. Protocol (First-Person Interactive)

1. **Simulator** role-plays the learner from **first-person beliefs** (it *believes* the misconception, reasons from it, and responds to probes accordingly) — not from an external narrator's perspective.
2. **Coach** runs its normal protocol unmodified (this is a regression test, not a demo).
3. **Transcript** is recorded verbatim.
4. **Judge** (a different role/pass, independent of both simulator and coach) scores the transcript on the 10 metrics below, 1–5 scale, **3 scoring passes averaged** to dampen judge variance.

---

## 4. Metric Mapping (TutorBench → Coach)

| # | TutorBench metric | Coach protocol equivalent | Pass bar (≥) |
| :--- | :--- | :--- | :--- |
| 1 | SF Source Faithfulness | Every explanation/claim traceable to S0 claim or coverage artifact | 3.5 |
| 2 | PER Personalization | Response adapts to D_w weakness + learner state, not syllabus default | 3.5 |
| 3 | APP Applicability | Ends with observable micro-behavioral probe, not "Does this make sense?" | 3.5 |
| 4 | VID Vividness | Uses counterexample shock / controlled variation / visual observation | 3.5 |
| 5 | LD Logical Depth | Causal chain before assertions (Shock-and-Deduce mandate) | 3.5 |
| 6 | FIT Fitness | Probe targets the diagnosed gap at the correct teaching budget | 3.5 |
| 7 | GND Groundedness | Generated practice item carries a valid `source_anchor` | 3.5 |
| 8 | DIV Diversity | Variation spans boundary dimensions, not one example pattern | 3.5 |
| 9 | ANS Answer Quality | Expected answer/explanation correct per S0 | 3.5 |
| 10 | CC Cross Concept | Includes a transfer modality or neighbor contrast | 3.0 |

---

## 5. Pass Criteria & Report

**Pass** if: all metrics ≥ their bar, **or** average score does not regress by more than 0.3 versus the previous recorded run for the same simulated learner.

**Report template** (appended to `evals/results/`):

```markdown
# Regression Report — {date} — {protocol version}
Simulated learner: {profile summary}
Result: PASS | FAIL | REGRESSION(-0.4)
| Metric | Score | Failure detail |
| SF | ... | ... |
Transcript highlights (2-3 evidence quotes).
Fixes applied: {list of protocol file changes}; re-run status: ...
```

On FAIL: fix the protocol files that caused the failure (e.g. a missing anchor rule, a teaching-budget violation), then re-run. Do NOT adjust the simulated learner to make the test pass.
