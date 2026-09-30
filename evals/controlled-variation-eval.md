# Evaluation Suite: Controlled Variation & Case Quality Gate

This benchmark verifies that every variation step mutates exactly ONE parameter, and any multi-variable mutation is rejected.

---

## Test Case 1: Dual-Variable Mutation Violation

### Candidate Variation Pair
- Baseline: `[1, 2, 3].includes(2)` -> `true`
- Mutated: `["a", "b", "c"].includes(4)` -> `false`

### Flawed Behavior (Auto-Fail)
- Accepts the mutation as a valid controlled test of `value_variation`.
- Confounders introduced: Both the array elements (numbers -> strings) and the search target (2 -> 4) changed simultaneously. The learner cannot attribute causality.

### Required Behavior (Pass)
- The Case Quality Gate rejects the pair:
  ```text
  ERROR: INVALID_CONTROLLED_VARIATION
  Variables mutated: [array_element_type, search_value] (Count: 2)
  Constraint: Delta count must equal exactly 1.
  ```
- Requires a two-step sequence holding one constant at each step:
  - Step 1: `[1, 2, 3].includes(4)` (Target value mutated only)
  - Step 2: `["1", "2", "3"].includes("4")` (Element and target types mutated together if testing string arrays, or separate element-type step).

---

## Test Case 2: Invariant Causal Attribution

### Candidate Variation Pair
- Baseline: `const fns = []; for (var i = 0; i < 3; i++) { fns.push(() => i); }`
- Mutated: `const fns = []; for (let i = 0; i < 3; i++) { fns.push(() => i); }`

### Required Behavior (Pass)
- Quality Gate inspects:
  - Variables changed: Declaration keyword only (`var` -> `let`).
  - Variables held constant: Loop limit (3), pushing mechanism, invocation structure.
  - Passes Quality Gate and generates valid Coverage Artifact for `loop_variable_binding`.
