# Concept Boundary Engine & Coverage Matrix Protocol

This document specifies the **Boundary Coverage Matrix**, the **Coverage Gap Detection** algorithm, and domain-specific behavioral dimension registries to guarantee zero omissions in technical knowledge coverage.

---

## 1. Prime Directive: Coverage Matrix Over Case Lists

A major defect in AI education is listing arbitrary examples without a mathematical proof of boundary completeness:
> **Listing 10 happy-path examples does not prove a concept is mastered.**
> **Completeness is proven only when every intrinsic behavioral dimension of the concept has a verified coverage artifact.**

```text
Concept Node
     │
     ▼
Domain Behavioral Dimensions Registry
     │
     ▼
Boundary Coverage Matrix (Evaluation of Gaps)
     │
     ▼
Coverage Gap Detection -> Enqueue Missing Dimension
     │
     ▼
Controlled Variation & Case Cluster Teaching
     │
     ▼
Verification & Audit
```

---

## 2. Standard Boundary Dimension Registry

Every technical domain defines its governing behavioral dimensions. A concept contract must map against these dimensions:

### 2.1 Universal Core Dimensions
1. `core_invariant`: The fundamental mathematical/runtime condition deciding truth.
2. `normal_behavior`: Nominal baseline execution without edge interference.
3. `value_variation`: Holding type and structure constant; changing search/input values.
4. `type_variation`: Holding value stringification constant; changing primitive data types.
5. `structural_variation`: Padded context, nesting, prefix/suffix additions.
6. `boundary_extremes`: Empty collections, boundary indices (0, -1, length), sparse slots.
7. `counterexamples`: Superficially identical structures that fail the invariant immediately.
8. `misconceptions`: Enticing mental traps refuted with falsifiable counter-code.
9. `neighboring_concepts`: Side-by-side trade-off debate against adjacent ecosystem APIs.
10. `real_world_failure`: Realistic production silent bugs caused by boundary misunderstanding.
11. `transfer`: Applying the invariant in a foreign, unprompted domain.

### 2.2 JavaScript Runtime Domain Extensions
- `primitive_vs_reference`: ECMAScript Object identity (SameValue / SameValueZero) vs primitive values.
- `type_coercion`: Abstract equality conversion rules (ToPrimitive, ToNumber, ToString).
- `special_primitives`: IEEE-754 primitives (`NaN`, `+0`, `-0`, `undefined`, `null`, `Symbol`).
- `sparse_slots`: Array holes (`new Array(3)`) vs explicitly assigned `undefined`.
- `prototype_chain`: Inherited properties vs own properties (`hasOwnProperty`).

---

## 3. The Boundary Coverage Matrix Schema

A Concept Boundary Contract must declare its explicit coverage matrix:

```yaml
concept_id: js-array-includes
coverage_audit:
  target_dimensions:
    - dimension: "primitive_baseline"
      status: "covered"
      test_case: "[1, 2, 3].includes(2)"

    - dimension: "type_mismatch_boundary"
      status: "covered"
      test_case: "[1, 2, 3].includes('2')"

    - dimension: "object_identity_reference"
      status: "covered"
      test_case: "[[1]].includes([1])"
      s0_fact: "ECMAScript SameValueZero algorithm: distinct object literals produce distinct object references; comparison evaluates to false."
      scaffolding_metaphor: "Distinct memory pointers (for beginner mental visualization only)."

    - dimension: "special_primitive_nan"
      status: "covered"
      test_case: "[NaN].includes(NaN)"

    - dimension: "special_primitive_signed_zero"
      status: "covered"
      test_case: "[+0].includes(-0)"
      s0_fact: "SameValueZero treats +0 and -0 as equal (unlike Object.is which differentiates them)."

    - dimension: "sparse_array_holes"
      status: "covered"
      test_case: "new Array(1).includes(undefined)"

    - dimension: "index_offset_boundaries"
      status: "covered"
      test_case: "[1, 2, 3].includes(2, 1) vs [1, 2, 3].includes(2, 2)"
```

---

## 4. Coverage Gap Detection Algorithm

When the Teaching Engine prepares a lesson:
1. **Matrix Inspection**: The engine loads the concept's `coverage_audit`.
2. **Gap Identification**: Any dimension flagged as `gap` or `partial` is enqueued into the immediate teaching queue.
3. **Instructional Generation**: The engine generates a single-variable controlled variation specifically targeting the missing dimension.
4. **Completion Guarantee**: The coach is forbidden from declaring "concept delivered" until 100% of defined target dimensions are marked `covered`.

---

## 5. Strict Separation: S0 Standard Fact vs. Scaffolding Metaphor

To maintain technical purity and avoid polluting standard engineering understanding:

### Rule 1: Normative Specifications Must Cite Standards (S0)
- **Object Reference Rule**: Never state as a formal rule that *"JavaScript compares memory pointers"*.
- **Standard Statement (ECMAScript §7.2.14 SameValueZero)**:
  > *If Type(x) is Object, return true if x and y are the same Object value (referencing the exact same object identity), otherwise return false. `[1] === [1]` evaluates to false because each array literal creates a newly allocated object identity.*

### Rule 2: Metaphors Must Be Declared as Scaffolding
- Metaphors (like "memory pointers" or "keycards") are strictly pedagogical tools for Beginners (Level 0-2). They must be formally tagged as `scaffolding_metaphor` and accompanied by the exact S0 fact.
