# Quality Rubrics & Evaluation Standards

This document establishes objective qualitative criteria for assessing explanations, predictions, implementations, and architectural trade-offs.

---

## 1. Explanation Rubric (Plain Language & Mechanism)

Evaluates whether the learner genuinely understands the physics of the system or is merely repeating technical buzzwords.

| Rating | Criteria |
| :--- | :--- |
| **Exemplary (Pass)** | Explains in clear, simple terms without relying on ungrounded jargon. Identifies cause-and-effect, runtime state transitions, memory boundaries, and why the system would fail without this design. |
| **Acceptable (Pass with Probe)** | Technically correct in conclusion, but leans on academic or framework terminology without immediate justification. The coach must prompt: *"Explain that without using the word [Term]."* |
| **Flawed (Fail)** | Confuses cause and effect (e.g. stating that `async/await` turns asynchronous code into multi-threaded synchronous execution). |
| **Superficial (Fail)** | Circular reasoning or value-judgments (e.g. *"We use TypeScript because it makes code safer and better"*). No concrete operational mechanics identified. |

---

## 2. Implementation Rubric (Code Production)

Evaluates learner-authored code in `E4: Implement` tasks.

| Criterion | Passing Standard | Red Flags (Auto-Fail) |
| :--- | :--- | :--- |
| **Functional Correctness** | Passes nominal cases and at least one boundary edge case (empty collection, network error, null/undefined). | Silent failures, unhandled promise rejections, swallowed exceptions. |
| **Scaffolding Independence** | Authored with `L0` (zero AI suggestions or boilerplate insertion). | Copying snippets verbatim from chat history; requesting AI completion. |
| **Clean Separation** | Logic is decoupled from side effects; mutation is explicit and constrained. | Global state pollution; mixing DOM mutation inside pure business logic. |
| **Debuggability** | Learner can explain why each line exists and what happens if line N is omitted. | Inability to answer: *"What would change if we deleted line 7?"* |

---

## 3. Trade-off & Architectural Decision Rubric

Evaluates responses in `/learn why` and `E5: Transfer` challenges.

A passing trade-off defense must demonstrate **The Law of Conservation of Misery**:
1. What benefit did we buy? (e.g. `O(1)` query speed).
2. What currency did we pay? (e.g. `O(N)` memory overhead, slower writes, cache invalidation complexity).
3. Under what conditions does this choice become wrong or disastrous? (e.g. *"If the dataset exceeds 10M records, this in-memory Map will crash the Node V8 heap with an OOM error"*).
