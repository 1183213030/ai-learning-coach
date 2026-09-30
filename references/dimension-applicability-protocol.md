# Dimension Applicability Protocol & Completeness Formula

This protocol establishes the formal mathematical rules for auditing behavioral dimensions against concepts to prevent arbitrary omission and false completeness.

---

## 1. The Core Defect: Arbitrary Boundary Listing

In conventional AI tutoring, an AI arbitrarily picks 3-5 examples, tests them, and claims 100% mastery:
> **Listing whatever examples come to mind is NOT engineering rigor.**
> **Every concept must be mapped against the domain's standardized Dimension Registry.**

---

## 2. Applicability Classification

Every registered dimension from the domain registry (`knowledge/dimensions/*.yaml`) must be evaluated for the target concept into exactly ONE of four applicability states:

```text
                     Dimension from Registry
                               │
            ┌──────────────────┼──────────────────┐
            ▼                  ▼                  ▼
       [required]         [optional]       [not_applicable]
    (Enters Denominator) (Enrichment Only) (Explicitly Excluded)
```

| Applicability State | Definition | Enters Completeness Denominator? | Enters Teaching Queue? |
| :--- | :--- | :--- | :--- |
| `required` | Essential behavioral invariant governing correct runtime execution. | **YES** | Mandatory |
| `optional` | Useful edge context, historical legacy, or advanced performance trivia. | NO | Context-dependent |
| `not_applicable` | Mechanically disconnected from the concept (with formal rationale). | NO | FORBIDDEN |
| `unknown` | Dimension has not yet been audited by the Knowledge Engine. | Triggers Audit Flag | Blocked |

---

## 3. The Completeness Formula

Knowledge Completeness is strictly bounded by the audited `required` set:

$$\text{Knowledge Completeness} = \frac{\sum \text{covered}(\text{required})}{\sum \text{all}(\text{required})} \times 100\%$$

### Hard Denominator Laws:
1. `not_applicable` dimensions **MUST NOT** be counted in either numerator or denominator.
2. `optional` dimensions **MUST NOT** inflate the required denominator.
3. If an AI lists 10 examples across only 2 required dimensions, Knowledge Completeness is **NOT** 100%; it is $2 / N_{\text{required}}$.

---

## 4. Formal Rationale Requirements

When marking a dimension as `required` or `not_applicable`, an explicit technical `reason` citing runtime mechanics is mandatory:

### Example: Array.prototype.includes
```yaml
boundary_matrix:
  - dimension: primitive_baseline
    applicability: required
    reason: "Defines normal value search baseline under SameValueZero."

  - dimension: object_identity
    applicability: required
    reason: "Objects are compared by reference identity; vital for preventing silent production bugs."

  - dimension: prototype_chain
    applicability: not_applicable
    reason: "Array.prototype.includes scans indexed numeric elements directly; it does not perform property lookup across the prototype chain."
```

By requiring explicit negative justifications for `not_applicable`, the AI coach is prevented from silently ignoring difficult or obscure edge cases.
