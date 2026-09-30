# Spaced Review System & Dynamic Regression Logic

This document specifies the spaced retrieval protocol, due queue scheduling, and automatic state regression rules.

---

## 1. Adaptive Retrieval Scheduling

Rather than using rigid SM-2 intervals designed for static flashcard memorization, review intervals in `ai-learning-coach` adapt to the **complexity of the engineering capability** and past failure evidence.

### Standard Progression Schedule

```text
Interval 1: Same session (Interleaved check at end of session)
Interval 2: Next day (+24h to +48h)
Interval 3: +5 to +7 days
Interval 4: +14 to +21 days
Interval 5: +30 to +45 days (Unlocks DURABLE upon passing)
```

---

## 2. Review Task Modalities (Rotation Protocol)

A review challenge must NEVER merely ask: *"What is the definition of X?"*

The coach rotates across 5 operational modalities during review:

1. **Blind Prediction (`predict_output`)**: Provide a small snippet involving edge cases; learner must trace output without running it.
2. **Reverse Bug Hunting (`find_regression`)**: Provide a working function modified with a subtle concurrency or memory flaw; learner must spot and fix it.
3. **Refactoring Under Constraint (`refactor_constraint`)**: Take a previous solution and ask to implement it without a specific built-in or with `O(1)` memory overhead.
4. **Blank Slate Reconstruction (`blind_implement`)**: Re-implement the atomic pattern in a clean scratch buffer.
5. **Cross-Domain Transfer (`masked_transfer`)**: Present the problem in a new technical framework or layer (e.g. from React state to Node stream buffering).

---

## 3. Dynamic Regression Triggers

Knowledge retention is volatile. Mastery states MUST regress when operational performance drops:

```text
+-----------------------+---------------------------------------+-----------------------------+
| Current State         | Failure Condition                     | New Degraded State          |
+-----------------------+---------------------------------------+-----------------------------+
| DURABLE               | Fails delayed retrieval challenge     | TRANSFERABLE                |
| TRANSFERABLE          | Fails cross-domain transfer (2 times) | INDEPENDENT                 |
| INDEPENDENT           | Requires L3-L5 hints on familiar task | GUIDED                      |
| GUIDED                | Cannot explain mechanism or predict   | EXPOSED (Full reset)        |
+-----------------------+---------------------------------------+-----------------------------+
```

### Action Upon Regression
1. **Log in `evidence.yaml`**: Mark `result: failed`, record detected misconception, and set `regression: true`.
2. **Flag in `learning-state.yaml`**: Add to `due_reviews` with priority `high`.
3. **Targeted Repair**: Do not re-teach the entire topic. Isolate the specific broken assumption (e.g. lexical vs dynamic scope) and run a 3-minute repair drill.
