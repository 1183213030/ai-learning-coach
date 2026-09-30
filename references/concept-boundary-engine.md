# Concept Boundary Engine & Executable State Protocol (Protocol V3.2.1)

This document specifies the **Boundary Coverage Matrix**, **Dimension Applicability**, the **Coverage Completeness Formula**, the **Coverage Gap Detection Algorithm**, **Coverage Artifacts**, and the **Case Quality Gate** to guarantee mathematical rigor and zero omissions in technical education.

---

## 1. Prime Directive: Boundary Coverage Over Case Counts

A fatal flaw in educational AI is assuming arbitrary examples constitute mastery:
> **Listing 10 happy-path examples does not prove a concept is mastered.**
> **Completeness is proven only when every applicable behavioral dimension of the concept possesses a verified Coverage Artifact that actively discriminates the boundary.**

```text
Concept Node
     │
     ▼
Domain Dimension Registry (universal.yaml / javascript.yaml)
     │
     ▼
Dimension Applicability Audit (required / optional / not_applicable with evidence)
     │
     ▼
Boundary Coverage Matrix (Audited Required Set)
     │
     ▼
Coverage Gap Detection (Identifies gaps & partials)
     │
     ▼
Teaching Queue with Priority (Schedules by cognitive priority)
     │
     ▼
Case Quality Gate (Enforces single semantic dimension delta)
     │
     ▼
Coverage Artifact & S0/S1 Traceability Chain
```

---

## 2. Dimension Applicability & The Completeness Formula

Every dimension from the domain registry must be classified for the target concept:

### 2.1 Applicability Classifications
- `required`: Essential behavioral dimension governing correct execution. Must enter the completeness denominator and teaching queue.
- `optional`: Enrichment or historical context. Does not inflate the required completeness denominator.
- `not_applicable`: Mechanically irrelevant to this concept. Requires a formal negative evidence chain (`claim_id`, `source_id`, `explanation`, `evidence_status: "verified"`).
- `unknown`: Unaudited dimension. Flags an incomplete concept contract.

### 2.2 Mathematical Completeness Formula

$$\text{Knowledge Completeness} = \frac{\sum \text{covered}(\text{required dimensions})}{\sum \text{all}(\text{required dimensions})} \times 100\%$$

**Hard Laws**:
1. `not_applicable` dimensions **MUST NOT** be counted in either numerator or denominator.
2. `optional` dimensions **MUST NOT** inflate the required denominator.
3. Completeness is strictly bounded by verified required dimensions, never arbitrary example counts.

---

## 3. The Boundary Coverage Matrix Schema

A Concept Boundary Contract must declare its explicit coverage matrix:

```yaml
concept_id: "js-array-includes"
boundary_matrix:
  - dimension: "primitive_baseline"
    applicability: "required"
    reason: "Defines normal value search baseline under SameValueZero."
    coverage:
      status: "covered"
      artifact_id: "artifact-includes-baseline"

  - dimension: "value_variation"
    applicability: "required"
    reason: "Changing target value is central to membership semantics."
    coverage:
      status: "covered"
      artifact_id: "artifact-includes-value-var"

  - dimension: "type_mismatch"
    applicability: "required"
    reason: "SameValueZero strictly checks types without coercion."
    coverage:
      status: "covered"
      artifact_id: "artifact-includes-type-var"

  - dimension: "object_identity"
    applicability: "required"
    reason: "Object operands are compared by reference identity, not structural fields."
    coverage:
      status: "covered"
      artifact_id: "artifact-includes-object-identity"

  - dimension: "special_nan"
    applicability: "required"
    reason: "Treating NaN as equal to NaN is the core differentiator from indexOf."
    coverage:
      status: "covered"
      artifact_id: "artifact-includes-nan"

  - dimension: "special_signed_zero"
    applicability: "required"
    reason: "SameValueZero treats +0 and -0 as equal."
    coverage:
      status: "covered"
      artifact_id: "artifact-includes-signed-zero"

  - dimension: "sparse_structure"
    applicability: "required"
    reason: "includes() treats sparse empty slots as undefined."
    coverage:
      status: "covered"
      artifact_id: "artifact-includes-sparse"

  - dimension: "prototype_chain"
    applicability: "not_applicable"
    rationale:
      claim_id: "includes-no-prototype-traversal"
      source_id: "ecma-262"
      section: "23.1.3.16 Array.prototype.includes"
      explanation: "Array.prototype.includes performs Get(O, Pk) exclusively on integer indices from 0 to len-1; it does not perform property lookup across the prototype chain."
      evidence_status: "verified"
```

---

## 4. Coverage Gap Detection Algorithm

When the Teaching Engine prepares an instructional plan:

```text
Algorithm: DetectCoverageGaps(concept_id, learner_id)
1. Load concept boundary_matrix and learner evidence ledger.
2. required_dims = boundary_matrix.filter(dim => dim.applicability === "required")
3. For each dim in required_dims:
     if dim.coverage.status !== "covered":
         enqueue(dim, status="gap", priority=dim.priority)
     else if learner_evidence[dim.id] < "independent":
         enqueue(dim, status="partial_mastery", priority=dim.priority)
4. Sort teaching_queue by:
     Priority (critical > high > medium > low)
     -> Prerequisites resolved first
     -> Learner cognitive budget
5. Return ordered teaching_queue slice for immediate session turn.
```

---

## 5. Case Quality Gate (Single Semantic Dimension Verification)

A major flaw in naive syntax checking is focusing on textual AST diffs rather than causal variables. The Case Quality Gate enforces that **exactly ONE causal semantic dimension** mutates between baseline and mutation:

```text
                     Candidate Variation Pair
                  (Baseline Case -> Mutated Case)
                               │
                               ▼
               Extract Causal Semantic Dimensions
                               │
               ┌───────────────┴───────────────┐
               ▼                               ▼
     Semantic Delta Count == 1       Semantic Delta Count > 1
               │                               │
               ▼                               ▼
      [GATE PASSED: VALID]            [GATE FAILED: REJECTED]
    Eligible for Artifact           Error: INVALID_CONTROLLED_VARIATION
```

### Validation Contract:
- `controlled_dimension`: The specific behavioral dimension under test (e.g. `reference_identity_relation`).
- `allowed_semantic_delta`: Exactly the 1 target dimension declared.
- `forbidden_semantic_delta`: All other semantic dimensions (e.g. data shapes, properties, operation types) must remain strictly invariant.
- **Example**: In `[[1]].includes([1])`, the mutated variable is NOT "search allocation"; it is the **identity relation between the element and the search argument** (`element === target` vs `element !== target`), while element shape and property values remain identical.

---

## 6. Coverage Artifact & Discriminative Power Specification

Every dimension marked `covered` must reference a concrete, immutable `Coverage Artifact` that actively discriminates between competing hypotheses:

```yaml
artifact_id: "artifact-includes-object-identity"
concept_id: "js-array-includes"
dimension_id: "object_identity"
claim_id: "same-value-zero-identity"

discriminates:
  - "element_and_search_share_same_identity (evaluates to true)"
  - "element_and_search_have_distinct_identities_with_same_shape (evaluates to false)"
discriminative_power: "strong"

case:
  baseline:
    input: "const o = { id: 1 }; [o].includes(o)"
    expected: true
  mutation:
    controlled_dimension: "reference_identity_relation"
    baseline_relation: "array[0] === search_target (true)"
    mutated_relation: "array[0] !== search_target (false)"
    input: "const o = { id: 1 }; [o].includes({ id: 1 })"
    expected: false

causal_explanation: "Under ECMAScript §7.2.14 SameValueZero, object literals allocate distinct Object identities. Comparison checks reference identity equality, not field structural equality."
scaffolding_metaphor: "Two separate keycards issued for two rooms with identical decor (for beginner visualization)."
misconception_target: "Assuming includes() performs deep field equality on objects."

quality_gate:
  single_semantic_dimension_verified: true
  controlled_dimension: "reference_identity_relation"
  forbidden_deltas_checked:
    - "object shape (held constant)"
    - "property values (held constant)"
    - "array length (held constant)"
  passed: true

observed_result:
  actual: false
  status: "verified"
```

---

## 7. Strict Separation: S0 Standard Fact vs. Scaffolding Metaphor

To maintain absolute engineering integrity:

### Rule 1: Normative Specifications Must Cite Standards (S0/S1)
- **Object Reference Rule**: Never state as a formal rule that *"JavaScript compares memory pointers"*.
- **Standard Statement (ECMAScript §7.2.14 SameValueZero)**:
  > *If Type(x) is Object, return true if and only if x and y refer to the exact same Object identity; otherwise return false. `[1] === [1]` evaluates to false because each array literal creates a newly allocated object identity.*

### Rule 2: Metaphors Must Be Declared as Scaffolding
- Metaphors (like "memory pointers" or "keycards") are strictly pedagogical tools for Beginners (Level 0-2). They must be formally tagged as `scaffolding_metaphor` and accompanied by the exact S0 fact.
