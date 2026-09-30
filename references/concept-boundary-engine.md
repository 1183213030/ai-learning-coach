# Concept Boundary & Expansion Engine

This document specifies the core pedagogical mechanism for expanding any concept into its **Minimal Complete Coverage** behavioral space.

---

## 1. The Core Philosophy: Boundary Space over Abstract Definitions

Traditional teaching introduces a concept through an abstract definition and a single happy-path example. The learner nods along, but has zero intuition about the concept's actual operational limits.

**The Golden Rule of Boundary Expansion**:
> **Do not merely explain what a concept means. Systematically unpack its entire behavioral surface: what makes it true, what keeps it true under mutation, what superficially resembles it but causes it to fail, and where its edge limits break.**

```text
Concept Node
     │
     ├── [ 1. The Core Governing Rule ] (The single invariant that decides truth)
     │
     ├── [ 2. Positive Nominal Cases ]  (Baseline conditions where it holds)
     │
     ├── [ 3. Structural Variations ]   (Mutations where it surprisingly STILL holds)
     │
     ├── [ 4. Counterexample Shocks ]  (Looks almost identical, but FAILS immediately)
     │
     ├── [ 5. Boundary & Extreme Limits] (Empty values, type coercion, special primitives)
     │
     ├── [ 6. Confusing Neighbor Contrast] (vs similar methods/keywords in ecosystem)
     │
     └── [ 7. Real Engineering Anchors] (Where this exact boundary boundary matters in production)
```

---

## 2. The 7-Dimension Minimal Complete Coverage Protocol

When teaching any concept, the coach automatically deduces its 7-dimensional behavioral space:

### Dimension 1: The Core Invariant
- What is the single, non-negotiable physical rule governing this mechanism?
- *Example (`includes`)*: Value must be located via SameValueZero comparison algorithm.
- *Example (`assertIn`)*: Target substring must appear contiguously inside the container.

### Dimension 2: Positive Nominal Cases (Baseline)
- The cleanest, zero-distraction example where the rule holds.
- `"admin"` in `"hello admin"` -> Pass.
- `[1, 2, 3].includes(2)` -> `true`.

### Dimension 3: Structural Variations (Invariance Testing)
- What changes can be made to surrounding data without breaking the invariant?
- Prefix additions: `"admin123"` -> Pass.
- Suffix additions: `"123admin"` -> Pass.
- Both ends padded: `"123admin456"` -> Pass.
- *Pedagogical Value*: Proves to the learner that location or padding does not invalidate the invariant.

### Dimension 4: Counterexample Shocks (The Crucial Step)
- **The most vital cognitive step in education**: Present an example that *visually resembles* the positive case, but *fails the underlying invariant*.
- `"admin"` in `"admmmmmin"` -> **FAIL**.
- `[1, 2, 3].includes("2")` -> **false** (Strict type boundary).
- `[[1]].includes([1])` -> **false** (Reference identity vs structural equality).
- *Pedagogical Prompt*: *"Notice how every single character of 'admin' exists in 'admmmmmin'. Why does the assertion fail? What specific rule was broken?"*
- *Result*: The learner autonomously deduces that **contiguity** is required, locking in the concept permanently.

### Dimension 5: Boundary & Extreme Limits (Edge Fuzzing)
- Empty string: `"" in "admin"` -> Pass. `"admin" in ""` -> Fail.
- Special IEEE-754 primitives: `[NaN].includes(NaN)` -> `true` (Unlike `indexOf`).
- Loose equality traps: `0 == false` -> `true`. `"" == false` -> `true`. `null == 0` -> `false`.

### Dimension 6: Confusing Neighbor Contrast
- Side-by-side comparison against the 2-3 most common alternatives:
  - `assertIn` vs `assertEqual` vs `regex match` vs `startswith`.
  - `Array.includes` vs `Array.indexOf` vs `Array.some` vs `Set.has`.
  - `==` vs `===` vs `Object.is`.

### Dimension 7: Real Engineering Anchors
- Why does knowing these edge cases matter in production?
  - *Example*: Checking user roles with `user.roles.includes("admin")` fails silently if API returns an array of objects `[{ name: "admin" }]` instead of strings.

---

## 3. Teaching Protocol: The "Shock and Deduce" Cycle

Never dump all 7 dimensions at once. Guide the learner through the **Shock and Deduce** progression:

```text
Step 1: Normal Case    -> Run baseline positive case.
Step 2: Variation      -> Add prefixes/suffixes; learner confirms it still works.
Step 3: Shock          -> Introduce Counterexample that intuitively looks right but fails.
Step 4: Deduction      -> Ask: "What exact invariant broke between Step 2 and Step 3?"
Step 5: Edge Fuzzing   -> Test empties, nulls, NaNs, or type shifts.
Step 6: Neighboring    -> Compare against alternative tool.
Step 7: Production Pin -> Apply to realistic API / bug scenario.
```
