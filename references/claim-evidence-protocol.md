# Claim-Evidence Protocol & S0 Traceability Chain (Protocol V3.2.1)

This protocol formalizes the rigorous link between formal engineering standards (S0), engine implementation facts (S1), normative claims, test cases, and empirical learner evidence.

---

## 1. Prime Architecture: The Traceability Triangle Chain

Knowledge in this system is never an unverified text snippet generated at AI discretion. It is structured into a bidirectional, tamper-evident verification chain:

```text
Normative Standard (S0) / Engine Implementation (S1)
         │
         ▼
  Normative Claim (claim_id + semantic_layer)
         │
         ▼
 Behavioral Dimension (dimension_id)
         │
         ▼
    Test Case (Single Semantic Dimension Variation)
         │
         ▼
     Observation (Actual Execution)
         │
         ▼
   Learner Evidence (Independent / Transfer)
```

### Upstream Verification (Why is this true?)
When a learner or auditor asks *"Why does this work this way?"*, the system traces upstream:
`Learner Evidence -> Test Case -> Behavioral Dimension -> Normative Claim -> Standard Source`.

### Downstream Proof (Why is this mastered?)
When the system assesses whether a learner has mastered a dimension, it verifies downstream:
`Standard Source -> Normative Claim -> Behavioral Dimension -> Discriminating Case -> Learner Prediction & Explanation`.

---

## 2. Semantic Layers & Evidence Hierarchy

To prevent specification boundary leakage (e.g. confusing language semantics with engine GC, or mixing ECMAScript with browser rendering), all claims must declare their explicit `semantic_layer`:

### 2.1 The Semantic Layer Boundary
- `ecmascript`: Formal ECMAScript language semantics (Environment Records, SameValueZero, Type Conversions).
- `html`: Host environment event loop, task queues, microtask checkpoints, message channels.
- `browser`: Browser rendering pipeline, style/layout/paint timing, requestAnimationFrame, DOM host objects.
- `engine`: Virtual machine implementation details (V8/SpiderMonkey garbage collection, JIT tiers, heap representations).
- `framework`: Application-level reactive engines (Vue effectScope, React scheduler/fiber).

### 2.2 Evidence Tier Hierarchy
- **Level S0 (Normative Standard)**: Authoritative, formal standard specifications (ECMA-262, WHATWG HTML Living Standard, W3C Recommendations).
- **Level S1 (Implementation Architecture)**: Authoritative engine or browser reference documentation (V8 Dev Blog, Chromium Design Docs, WebKit Source).
- **Level S2 (Framework & Platform Specs)**: Official framework core documentation and accepted RFCs (Vue Core RFCs, React Documentation).
- **Level S3 (Secondary Synthesis)**: Curated community references (MDN Web Docs).

**Hard Separation Invariant**:
- Never claim an S1 engine implementation fact (e.g. V8 generational GC reachability) is an S0 ECMAScript language rule.
- Never use ECMAScript (S0) to explain browser rendering steps or microtask checkpoint host scheduling (WHATWG HTML S0).

---

## 3. Normative Claims Structure

A `claim` is an irreducible, falsifiable technical statement anchored directly in a standard or implementation source:

```yaml
claims:
  - id: "same-value-zero-identity"
    semantic_layer: "ecmascript"
    source_id: "ecma-262"
    level: "S0"
    section: "7.2.14 SameValueZero"
    claim_text: "If Type(x) is Object, SameValueZero returns true if and only if x and y refer to the exact same Object value."

  - id: "closure-lexical-retention"
    semantic_layer: "ecmascript"
    source_id: "ecma-262"
    level: "S0"
    section: "9.1.2 Environment Records"
    claim_text: "Function instances retain an explicit outer reference to the lexical Environment Record in which they were evaluated."

  - id: "v8-gc-reachability"
    semantic_layer: "engine"
    source_id: "v8-garbage-collector"
    level: "S1"
    section: "Orinoco GC Heap Tracing"
    claim_text: "Memory occupied by an Environment Record cannot be reclaimed by garbage collection if any reachable function object holds an active reference to that record."
```

---

## 4. Evidence Chain for `not_applicable` Classifications

Deciding that a dimension is NOT applicable is a formal claim that requires proof:
> **"Not applicable" is not an arbitrary omission. It is an audited negative invariant.**

Every `not_applicable` dimension in a Boundary Matrix must contain an evidence chain:

```yaml
- dimension: "prototype_chain"
  applicability: "not_applicable"
  rationale:
    claim_id: "includes-no-prototype-traversal"
    source_id: "ecma-262"
    section: "23.1.3.16"
    explanation: "Array.prototype.includes performs Get(O, Pk) for integer indices 0 to len-1; it does not traverse named prototype property access algorithms."
    evidence_status: "verified"
```

---

## 5. Scaffolding Metaphor Isolation

To maintain technical purity, metaphors used to assist beginners MUST NOT be stated as normative truths:

| Element | Normative Claim (S0/S1) | Scaffolding Metaphor (Level 0-2 Only) |
| :--- | :--- | :--- |
| Object Comparison | Distinct object literals produce distinct object identities per SameValueZero. | "Different memory pointers" or "Two houses built from the same blueprint". |
| Closure Scope | Execution context retains a reference to its outer Environment Record. | "A backpack carried by the inner function containing variables". |
| Event Loop | Microtask queue drains completely before the next task or rendering step. | "A VIP queue that cuts ahead of the regular ticket line". |

**Rule**: Every `scaffolding_metaphor` must accompany a normative `claim_id` and must be phased out before final L0 capability verification.
