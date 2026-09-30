# Evaluation Suite: Claim-Source Traceability & S0/S1 Layer Isolation (Protocol V3.2.1)

This benchmark verifies that every normative rule is anchored to an appropriate standard source (S0) or implementation source (S1), semantic layers are strictly isolated, and conceptual metaphors are segregated as scaffolding.

---

## Test Case 1: The "ECMAScript GC" Level Violation

### Candidate Explanation
> "Under the ECMAScript language specification, the Garbage Collector cannot free outer variables if an inner closure exists."

### Flawed Behavior (Auto-Fail)
- Conflates ECMAScript language semantics (Environment Record retention S0) with Virtual Machine GC implementation algorithms (V8/SpiderMonkey S1).
- ECMAScript specifies observable runtime evaluation semantics, not specific garbage collection algorithms.

### Required Behavior (Pass)
- Strictly separates the layers:
  - **S0 (ECMAScript §9.1.2)**: "A function retains a reference to its outer lexical Environment Record."
  - **S1 (V8 Engine Implementation)**: "As long as a closure function remains reachable on the heap, V8 GC tracing preserves the referenced Environment Record."

---

## Test Case 2: The "Memory Pointer" Metaphor Pollution

### Candidate Explanation
> "In JavaScript, `[[1]].includes([1])` returns false because JavaScript arrays compare memory pointers in the heap."

### Flawed Behavior (Auto-Fail)
- Quotes an informal mental model ("memory pointer") as an official ECMAScript rule.

### Required Behavior (Pass)
- Cites ECMAScript §7.2.14 `SameValueZero`:
  > "Under ECMAScript §7.2.14 SameValueZero, object literals create distinct Object identities. Reference identity comparison evaluates to false."
- Labels "memory pointer" strictly as a beginner mental scaffolding metaphor:
  `scaffolding_metaphor: "Think of it as two separate keycards to identical hotel rooms."`

---

## Test Case 3: Unverified `not_applicable` Exclusion

### Candidate Contract
An agent marks `prototype_chain` as `not_applicable` for `Array.prototype.includes` with `artifact_id: null` and no evidence.

### Flawed Behavior (Auto-Fail)
- Treats "not applicable" as an unverified negative assumption without evidence.

### Required Behavior (Pass)
- Requires a formal negative rationale citing standards:
  - `claim_id`: "includes-no-prototype-lookup"
  - `source_id`: "ecma-262"
  - `section`: "23.1.3.16"
  - `evidence_status`: "verified"
