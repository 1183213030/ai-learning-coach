# Concept Boundary & Expansion Engine (Contract Protocol)

This document specifies the **Concept Boundary Contract**: the formal contract between Knowledge Registry and the Teaching Engine that guarantees zero omissions in conceptual behavioral coverage.

---

## 1. The Core Philosophy: Boundary Space over Abstract Definitions

Traditional AI teaching introduces a concept through an abstract definition and a single happy-path example. The learner nods along, but has zero intuition about the concept's actual operational limits.

**The Golden Law of Boundary Expansion**:
> **Do not merely explain what a concept means. Systematically unpack its entire behavioral surface: what makes it true, what keeps it true under mutation, what superficially resembles it but causes it to fail, and where its edge limits break.**
>
> **教学可以渐进，但概念边界不能遗漏。不要要求每一次解释都完整；要要求每一个概念最终都有完整的行为边界覆盖。**

---

## 2. The Formal Concept Boundary Contract Schema

Every concept registered in the system must conform to the following structured contract. The Teaching Engine draws strictly from these fields rather than improvising uncurated examples on the fly:

```yaml
concept:
  id: string
  name: string
  core_invariant: string           # The single physical/mathematical rule deciding truth

  behavioral_space:
    baseline:                      # Baseline nominal condition where invariant holds cleanly
      input: string
      expected: any
      rationale: string

    positive_cases:                # Standard valid conditions
      - input: string
        expected: any
        rationale: string

    controlled_variations:         # Strictly single-variable mutation chain
      - step: integer
        variable_changed_only: string # Explicitly state the single delta
        input: string
        expected: any
        rationale: string

    counterexample_shocks:         # Visually resembles positive case, but fails invariant immediately!
      - input: string
        expected: any
        shock_reason: string
        pedagogical_prompt: string

    boundary_cases:                # Empty values, special IEEE-754 primitives, type coercion limits
      - input: string
        expected: any
        boundary_type: string
        rationale: string

    common_misconceptions:         # Mental traps explicitly articulated and refuted with counter-code
      - trap: string
        counter_proof: string

    confusing_neighbor_contrast:   # Side-by-side differentiation against adjacent ecosystem tools
      - neighbor: string
        core_difference: string
        when_to_use_which: string

    real_world_anchors:            # Production scenarios and silent bug vectors
      - scenario: string
        trap_in_production: string
        correct_pattern: string

    failure_modes:                 # What breaks downstream if this concept is misunderstood?
      - symptom: string
        root_cause: string

    transfer_cases:                # Applying invariant in an unfamiliar domain with keywords omitted
      - novel_domain: string
        task: string
        expected_deduction: string
```

---

## 3. Strict Controlled Variation Protocol

To prevent cognitive overload and guarantee accurate causal attribution:
1. **The Delta Constraint**: Between `step N` and `step N+1`, exactly ONE parameter may change.
2. **Forbidden**: Mutating array values, array types, and search values simultaneously.
3. **Mandatory Sequence**:
   - `Baseline` ->
   - `Mutate Value Only` ->
   - `Mutate Argument Type Only` ->
   - `Mutate Element Type Only` ->
   - `Mutate Reference Structure Only` ->
   - `Mutate Special Primitive Only`.

---

## 4. Teaching Progression: The "Shock and Deduce" Cycle

The Teaching Engine executes the contract in sequenced phases:

```text
Phase 1: Baseline & Variation -> Observe invariant holding under controlled single shifts.
Phase 2: Counterexample Shock -> Near-miss scenario fails; learner deduces the invariant.
Phase 3: Boundary Fuzzing     -> Test empties, nulls, NaNs, or edge coercions.
Phase 4: Neighbor Debate      -> Contrast against alternative API / keyword.
Phase 5: Production Grounding -> Trace realistic silent bug in real project.
```
