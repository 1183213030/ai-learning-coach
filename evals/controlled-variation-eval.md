# Evaluation Suite: Controlled Variation & Case Quality Gate (Protocol V3.2.1)

This benchmark verifies that every variation step mutates exactly ONE causal semantic dimension, and any multi-dimension mutation is rejected by the Case Quality Gate.

---

## Test Case 1: Multi-Semantic Dimension Mutation Violation

### Candidate Variation Pair
- Baseline: `[1, 2, 3].includes(2)` -> `true`
- Mutated: `["a", "b", "c"].includes(4)` -> `false`

### Flawed Behavior (Auto-Fail)
- Accepts the mutation because it only changes 2 tokens.
- Fails to detect that both the array element type and the target search value changed simultaneously. The learner cannot attribute causality.

### Required Behavior (Pass)
- The Case Quality Gate rejects the pair:
  ```text
  ERROR: INVALID_CONTROLLED_VARIATION
  Semantic dimensions mutated: [array_element_type, search_value] (Count: 2)
  Constraint: Exactly ONE causal semantic dimension may mutate.
  ```
- Requires a two-step sequence:
  - Step 1: Mutate search value only (`[1, 2, 3].includes(4)`).
  - Step 2: Mutate array element type (`['1', '2', '3'].includes('2')`).

---

## Test Case 2: Semantic Single Dimension vs. Syntax Diffs

### Candidate Variation Pair
- Baseline: `Promise.resolve().then(() => log.push('task'))`
- Mutated: `queueMicrotask(() => log.push('task'))`

### Flawed Behavior (Auto-Fail)
- The syntax checker fails because `Promise`, `resolve`, and `then` were replaced by `queueMicrotask` (textual diff > 1).

### Required Behavior (Pass)
- The Case Quality Gate recognizes semantic equivalence:
  - Controlled Dimension: `microtask_scheduling_mechanism`
  - Callback body and execution context held strictly invariant.
  - Passes the gate as a valid semantic controlled variation.
