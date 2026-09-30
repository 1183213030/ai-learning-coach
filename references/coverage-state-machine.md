# Coverage & Capability State Machine Protocol

This protocol formally decouples **Knowledge Coverage (系统知识完整)**, **Teaching Coverage (实际教学实施)**, and **Learner Evidence (学习者独立能力)** into independent, verifiable state machines.

---

## 1. The Tri-Completeness Decoupling

A catastrophic mistake in educational AI is equating *"I explained it"* with *"the student mastered it"*:
> **Explaining everything does not mean the user learned it.**
> **Knowing 100% of facts does not mean the teaching covered all of them in this session.**
> **These three dimensions must be tracked independently.**

```text
┌───────────────────────────────┐
│     Knowledge Coverage        │  (Does the syllabus / YAML define the complete space?)
│  unknown -> partial -> covered│
└──────────────┬────────────────┘
               │
               ▼
┌───────────────────────────────┐
│     Teaching Coverage         │  (Did the coach present & unpack this dimension to user?)
│ pending -> in_progress -> done│
└──────────────┬────────────────┘
               │
               ▼
┌───────────────────────────────┐
│     Learner Evidence          │  (Can the user predict and apply under zero AI hints L0?)
│ not_attempted -> independent  │
└───────────────────────────────┘
```

---

## 2. State Machine Definitions

### 2.1 Knowledge Coverage State Machine (Specification Level)
Measures whether the concept contract has mapped and verified all applicable dimensions against standard specifications:
- `unknown`: Dimension has not yet been audited.
- `partial`: Dimension has a defined case, but lacks full S0 claim linkage or variation verification.
- `covered`: Dimension possesses an audited, verified test case linked to an S0 claim.

### 2.2 Teaching Coverage State Machine (Pedagogical Session Level)
Measures the actual instructional delivery across conversational sessions:
- `pending`: Dimension sits in the Teaching Queue awaiting its scheduled phase.
- `in_progress`: Active controlled variation or counterexample shock currently under discussion.
- `delivered`: Single-variable mutation and causal explanation successfully completed in session.

### 2.3 Learner Evidence State Machine (Mastery Level)
Measures unassisted empirical capability demonstrated by the learner:
- `not_attempted`: Learner has not been probed on this dimension.
- `attempted`: Learner attempted but failed or required substantial hints (L2/L3).
- `supported`: Learner succeeded with minimal conceptual scaffolding (L1).
- `independent`: Learner solved and explained correctly with zero AI intervention (`L0`).
- `transfer_verified`: Learner correctly diagnosed and applied the invariant in an unfamiliar novel domain.

---

## 3. The True Mastery Threshold

A concept is marked as **True Engineering Mastery** if and only if:

$$\text{Knowledge Coverage} = \text{covered} \quad \land \quad \text{Learner Evidence} \ge \text{independent}$$

```text
Status Display Paradigm:
┌─────────────────────────────────────────────────────────┐
│ Concept: Array.prototype.includes                       │
│ 知识边界 (Knowledge): 100% (8/8 Required Dimensions)    │
│ 教学覆盖 (Teaching):  75%  (6/8 Delivered in Sessions)   │
│ 独立能力 (Capability): 50%  (4/8 L0 Independent Proof)   │
│ 下一步动作: 针对 object_identity 调度迁移实战测试        │
└─────────────────────────────────────────────────────────┘
```

---

## 4. Reversible Regression Safeguard

Learner Evidence states are strictly reversible:
- If a learner achieves `independent` on `object_identity` in isolation;
- But subsequently fails an unassisted complex project task (e.g. JWT role array matching);
- The state machine immediately fires:
  ```text
  EVENT: REGRESSION DETECTED on dimension [object_identity]
  TRANSITION: independent -> supported
  ACTION: Enqueue targeted counterexample shock in next session
  ```
- The Knowledge Coverage remains `covered`, but Capability drops until re-verified.
