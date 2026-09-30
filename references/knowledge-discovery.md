# Knowledge Discovery & Source Strategy

This document specifies how the coach discovers, filters, validates, and ranks learning sources across the Web, Local Library, and Project Codebase.

---

## 1. The Three Knowledge Ingress Pillars

When initiating study in any technical domain, the coach ingests knowledge from three distinct pillars:

```text
                  Knowledge Ingress
                          │
       ┌──────────────────┼──────────────────┐
       ↓                  ↓                  ↓
  Local Library      Web Research     Project Context
 (Primary Ground)   (Authoritative)    (Empirical Ground)
```

1. **Local Library (`library/`)**: Priority 1. Ingests user-supplied markdown files, textbooks, PDFs, and documentation saved in `library/<domain>/`.
2. **Web Research (Authoritative Retrieval)**: Priority 2. Fetches official specifications, release notes, and canonical documentation to fill gaps or construct domain roadmaps.
3. **Project Context (`git diff` & Codebase)**: Priority 3. Extracts real-world application contexts, architectures, and empirical bugs to ground theory in practice.

---

## 2. Authoritative Source Ranking (S0 to S5)

The coach strictly grades all technical information by source tier. Never cite a low-tier blog post when a higher-tier specification exists.

| Tier | Category | Concrete Examples | Verification Reliability |
| :--- | :--- | :--- | :--- |
| **S0** | **Official Specifications & Living Standards** | ECMAScript Spec (tc39), W3C Recommendations, IETF RFCs, MDN Web Docs, Official Handbooks (Vue, React, TypeScript, Node.js, ISTQB). | Absolute Ground Truth (100%) |
| **S1** | **Authoritative Academic & Industry Standard Textbooks** | CSAPP, Dragon Book, Designing Data-Intensive Applications (Kleppmann), Software Testing (Myers). | Extremely High (95%) |
| **S2** | **Vetted Professional Courses & Published Books** | O'Reilly, Manning, Frontend Masters, official vendor certification syllabi. | High (85%) |
| **S3** | **Peer-Reviewed Community Architecture Papers** | High-reputation engineering blogs (Cloudflare Blog, Uber Engineering, V8 Dev Blog, Web.dev). | Medium-High (75%) |
| **S4** | **Informal Community Articles & Discussions** | Medium, Dev.to, Zhihu, Juejin, StackOverflow threads. | Use only for practical troubleshooting; never for fundamental mechanism definitions. |
| **S5** | **AI Internal Model Syntheses** | Raw parametric memory of the LLM. | Subject to hallucination; must be cross-referenced with S0/S1. |

---

## 3. Strict Boundary: SOURCE FACT vs. TEACHER EXPLANATION

A catastrophic failure in technical education is conflating pedagogical metaphors with system reality. The coach enforces a hard wall between:

### 3.1 SOURCE FACT (System Truth)
- Objective facts defined by runtime standards or specifications.
- **Rule**: Must be stated accurately with zero simplification errors.
- **Example**: *"According to ECMAScript §9.4, an execution context's LexicalEnvironment consists of an Environment Record and a null/outer reference. Closures keep this record reachable on the V8 heap."*

### 3.2 TEACHER EXPLANATION (Cognitive Scaffolding)
- Metaphors, analogies, and mental models designed to bridge intuition.
- **Rule**: Must be explicitly declared as a scaffolding tool, along with its limits.
- **Example**: *"To build a working intuition, picture the function carrying a backpack of variables wherever it travels. Note: This metaphor breaks down when two functions share the same outer scope, because they actually share the exact same reference rather than individual backpacks."*

---

## 4. The `/learn search` Protocol

When the learner types `/learn search [topic]` (e.g. `/learn search web security`):
1. **Query Formulation**: Search for official specifications, canonical roadmaps, and S0/S1 references.
2. **Gap Analysis**: Check if local materials exist under `library/<topic>/`.
3. **Synthesis Output**:
   - High-level domain topology (Prerequisites -> Fundamentals -> Production Engineering).
   - Ranked list of canonical S0/S1 documentation links.
   - Recommended entry point aligned with the user's `learner-profile.md`.
4. **Manifest Generation**: Offer to write the findings into `templates/source-manifest.yaml`.
