# Concept Boundary Engine & Executable State Protocol (Protocol V3.2)

This document specifies the **Boundary Coverage Matrix**, **Dimension Applicability**, the **Coverage Completeness Formula**, the **Coverage Gap Detection Algorithm**, **Coverage Artifacts**, and the **Case Quality Gate** to guarantee mathematical rigor and zero omissions in technical education.

---

## 1. Prime Directive: Boundary Coverage Over Case Counts

A fatal flaw in educational AI is assuming arbitrary examples constitute mastery:
> **Listing 10 happy-path examples does not prove a concept is mastered.**
> **Completeness is proven only when every applicable behavioral dimension of the concept possesses a verified Coverage Artifact.**

```text
Concept Node
     │
     ▼
Domain Dimension Registry (universal.yaml / javascript.yaml)
     │
     ▼
Dimension Applicability Audit (required / optional / not_applicable)
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
Case Quality Gate (Enforces single-variable delta constraint)
     │
     ▼
Coverage Artifact & S0 Traceability Chain
```

---

## 2. Dimension Applicability & The Completeness Formula

Every dimension from the domain registry must be classified for the target concept:

### 2.1 Applicability Classifications
- `required`: Essential behavioral dimension governing correct execution. Must enter the completeness denominator and teaching queue.
- `optional`: Enrichment or historical context. Does not inflate the required completeness denominator.
- `not_applicable`: Mechanically irrelevant to this concept. Requires an explicit negative technical rationale.
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
    reason: "includes() operates solely on indexed numeric properties and does not traverse the prototype chain."
    coverage:
      status: "not_applicable"
      artifact_id: null
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

## 5. Case Quality Gate (Single-Variable Verification)

To guarantee that variations provide unconfounded causal learning, every candidate case must pass the automated **Case Quality Gate**:

```text
                     Candidate Variation Pair
                  (Baseline Case -> Mutated Case)
                               │
                               ▼
                    Extract Changed Variables
                               │
               ┌───────────────┴───────────────┐
               ▼                               ▼
       Delta Count == 1                 Delta Count > 1
               │                               │
               ▼                               ▼
      [GATE PASSED: VALID]            [GATE FAILED: REJECTED]
    Eligible for Artifact           Error: INVALID_CONTROLLED_VARIATION
```

### Validation Invariants:
1. Exactly ONE parameter may mutate between baseline and test case.
2. Holding array structure, input types, and search values constant while mutating only the target variable.
3. If two variables change simultaneously (e.g. changing both target type and target value), the case is rejected and forbidden from serving as a Coverage Artifact.

---

## 6. Coverage Artifact Specification

Every dimension marked `covered` must reference a concrete, immutable `Coverage Artifact`:
- `artifact_id`: Unique identifier.
- `claim_id`: Standard S0 claim reference.
- `case`:
  - `baseline`: Input and expected outcome.
  - `mutation`: Input, expected outcome, and `changed_only` declaration.
- `causal_explanation`: Technical explanation derived from the S0 standard.
- `scaffolding_metaphor`: Tagged beginner intuition (isolated from S0).
- `misconception_target`: The specific mental trap broken by this case.
- `quality_gate`: Record of single-variable verification.

---

## 7. Strict Separation: S0 Standard Fact vs. Scaffolding Metaphor

To maintain absolute engineering integrity:

### Rule 1: Normative Specifications Must Cite Standards (S0)
- **Object Reference Rule**: Never state as a formal rule that *"JavaScript compares memory pointers"*.
- **Standard Statement (ECMAScript §7.2.14 SameValueZero)**:
  > *If Type(x) is Object, return true if and only if x and y refer to the exact same Object identity; otherwise return false. `[1] === [1]` evaluates to false because each array literal creates a newly allocated object identity.*

### Rule 2: Metaphors Must Be Declared as Scaffolding
- Metaphors (like "memory pointers" or "keycards") are strictly pedagogical tools for Beginners (Level 0-2). They must be formally tagged as `scaffolding_metaphor` and accompanied by the exact S0 fact.
