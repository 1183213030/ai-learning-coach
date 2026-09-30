# Dimension Applicability Protocol & Completeness Formula (Protocol V3.2.1)

This protocol establishes the formal mathematical rules for auditing behavioral dimensions against concepts to prevent arbitrary omission, false completeness, and unverified exclusions.

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
    (Enters Denominator) (Enrichment Only) (Audited Evidence Chain)
```

| Applicability State | Definition | Enters Completeness Denominator? | Enters Teaching Queue? |
| :--- | :--- | :--- | :--- |
| `required` | Essential behavioral invariant governing correct runtime execution. | **YES** | Mandatory |
| `optional` | Useful edge context, historical legacy, or advanced performance trivia. | NO | Context-dependent |
| `not_applicable` | Mechanically disconnected from the concept (with formal evidence chain). | NO | FORBIDDEN |
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

## 4. Evidence Chain for `not_applicable` Classifications

Deciding that a dimension is NOT applicable is a formal claim that requires proof:
> **"Not applicable" is not an arbitrary omission. It is an audited negative invariant.**

Every `not_applicable` dimension in a Boundary Matrix must contain an evidence chain:

```yaml
boundary_matrix:
  - dimension: "prototype_chain"
    applicability: "not_applicable"
    rationale:
      claim_id: "includes-no-prototype-lookup"
      source_id: "ecma-262"
      section: "23.1.3.16 Array.prototype.includes"
      explanation: "Array.prototype.includes performs Get(O, Pk) exclusively on integer indices from 0 to len-1; it does not perform property lookup across the prototype chain."
      evidence_status: "verified"
```

---

## 5. Algorithmic Applicability via Registry Signals

To eliminate ad-hoc AI guessing, dimensions in the Domain Registry define matching signals:
- `semantic_layer`: Restricts matching to concepts operating at that architectural level.
- `applicability_signals`: Keywords/mechanisms whose presence triggers `required` candidacy (e.g. `membership`, `equality`).
- `exclusion_signals`: Keywords/mechanisms that validate `not_applicable` exclusion (e.g. `pure_arithmetic`, `prototype_independent`).
- `prerequisite_dimensions`: Mandatory prerequisite dimensions that must be audited prior to this dimension.
