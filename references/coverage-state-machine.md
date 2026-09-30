# Coverage & Capability State Machine Protocol (Protocol V3.2.1)

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

## 3. Two-Tier Mastery Definitions

To prevent conflating basic independent understanding with complex novel transfer:

### Tier 1: Concept Mastery (概念独立掌握)
The learner can solve and explain all required dimensions independently without hints:

$$\text{Concept Mastery} \iff \text{Knowledge Coverage} = 100\% \quad \land \quad \forall d \in \text{required}, \text{Evidence}(d) \ge \text{independent}$$

### Tier 2: Engineering Mastery (工程实战精通)
The learner has achieved Concept Mastery AND successfully transferred the invariant to unprompted real-world engineering code:

$$\text{Engineering Mastery} \iff \text{Concept Mastery} \quad \land \quad \forall d \in \text{transfer\_required}, \text{Evidence}(d) = \text{transfer\_verified}$$

```text
Status Display Paradigm:
┌──────────────────────────────────────────────────────────────┐
│ Concept: Array.prototype.includes                            │
│ 知识边界 (Knowledge):      100% (8/8 Required Dimensions)    │
│ 教学实施 (Teaching):        100% (8/8 Delivered in Sessions)  │
│ 概念掌握 (Concept Mastery): 100% (8/8 Independent Proof L0)  │
│ 工程精通 (Engineering):     75%  (3/4 Transfer Verified)      │
│ 下一步动作: 针对 object_identity 调度真实生产环境 JWT 角色排查 │
└──────────────────────────────────────────────────────────────┘
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
- The Knowledge Coverage remains `covered`, but Concept Mastery drops until re-verified.
