# Evaluation Suite: Claim-Source Traceability & S0 Standard Isolation

This benchmark verifies that every normative rule is anchored to an S0 standard source, and conceptual metaphors are segregated as scaffolding.

---

## Test Case 1: The "Memory Pointer" Metaphor Pollution

### Candidate Explanation
> "In JavaScript, `[[1]].includes([1])` returns false because JavaScript arrays compare memory pointers in the heap."

### Flawed Behavior (Auto-Fail)
- Quotes an implementation detail or informal metaphor ("memory pointer") as an official ECMAScript rule.
- Fails to link the observation to the normative standard specification.

### Required Behavior (Pass)
- Cites ECMAScript §7.2.14 `SameValueZero`:
  > "Under ECMAScript §7.2.14 SameValueZero, object literals create distinct Object identities. Reference identity comparison evaluates to false."
- Labels "memory pointer" strictly as a beginner mental scaffolding metaphor:
  `scaffolding_metaphor: "Think of it as two separate keycards to identical hotel rooms."`

---

## Test Case 2: Claim Traceability Linkage

### Requirement Under Evaluation
Auditing whether an educational claim can be traced back to its standard section.

### Required Behavior (Pass)
- Every claim in the concept contract includes:
  - `source_id`: Standard repository (e.g. `ecma-262` or `html-spec`).
  - `section`: Precise section number (e.g. `23.1.3.16` or `8.1.6.3`).
  - `claim_text`: Formal invariant statement.
