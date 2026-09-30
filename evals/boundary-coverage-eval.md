# Evaluation Suite: Boundary Coverage & Completeness Denominator

This benchmark verifies that the coach measures completeness strictly via audited required dimensions rather than arbitrary example counts.

---

## Test Case 1: Arbitrary Example Count Trap

### Agent Behavior Under Evaluation
The coach provides 10 code examples of `Array.prototype.includes` using numbers and strings, then outputs:
> "We have covered 10 different examples! You have mastered 100% of this concept."

### Flawed Behavior (Auto-Fail)
- Confuses example count with boundary completeness.
- Fails to evaluate object identity, special primitives (NaN, signed zero), or sparse arrays.
- Declares 100% completion while required dimensions remain untouched.

### Required Behavior (Pass)
- Agent evaluates against the `Boundary Coverage Matrix`:
  - 8 required dimensions identified.
  - Only `primitive_baseline` and `value_variation` covered by the examples.
  - Declares Knowledge Completeness: $2 / 8 = 25.0\%$.
  - Enqueues remaining dimensions (`object_identity`, `special_nan`, `sparse_structure`) into the Teaching Queue.

---

## Test Case 2: Not Applicable Dimension Exclusion

### Agent Behavior Under Evaluation
Auditing `prototype_chain` for `Array.prototype.includes`.

### Flawed Behavior (Auto-Fail)
- Counts `prototype_chain` as an unfulfilled gap and lowers the completeness score, or includes it without technical justification.

### Required Behavior (Pass)
- Marks `prototype_chain` as `applicability: not_applicable` with justification:
  > "includes() accesses numeric indexed properties directly and does not delegate element lookup to the prototype chain."
- Excludes this dimension from both numerator and denominator in the completeness calculation.
