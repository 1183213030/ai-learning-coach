# Adaptive Curriculum Decision Engine (V2.2)

This document specifies the highest-priority arbitration logic: **Learner State over Curriculum State**.

---

## 1. The Real-World Priority Cascade

Curriculum progress is subordinate to learner context. When determining the immediate learning action, the engine evaluates conditions in strict order:

```text
Incoming Learner Signal
           │
           ├─► Priority 1: Real-World Urgent Problem / Bug?
           │      └── Action: PAUSE CURRICULUM. Solve and extract lesson from project context.
           │
           ├─► Priority 2: Energy & Time Constraint ("15 mins / exhausted")?
           │      └── Action: SKIP NEW CHAPTERS. Switch to micro-retrieval on recent weak spot.
           │
           ├─► Priority 3: Confirmed Retention Regression (Due review failed)?
           │      └── Action: HALT ADVANCEMENT. Execute targeted 5-minute repair drill.
           │
           ├─► Priority 4: Missing Prerequisite Discovered?
           │      └── Action: INJECT REPAIR NODE. Resolve upstream concept before proceeding.
           │
           └─► Priority 5: Normal Flow (Nominal conditions satisfied)
                  └── Action: Generate single active lesson for next capability frontier.
```

---

## 2. Adaptive Time & Energy Budgets

When the learner provides energy or time signals, the system dynamically scales the interaction shape:

### 2.1 The "15-Minute / Low Energy" Mode
- **Prohibited**: Introducing new foundational frameworks, heavy derivations, or long multi-part lessons.
- **Protocol**:
  1. Retrieve the single most volatile concept from `learning-state.yaml` (e.g. boundary values).
  2. Deliver 1 concrete retrieval challenge (e.g. identify 3 boundaries for a coupon code).
  3. Close with a 1-sentence takeaways summary and immediate log.

### 2.2 The "Work Interrupt" Mode
- When the user says *"Skip the textbook today, I hit an auth token refresh bug in my project"*:
  1. Freeze the current textbook position in `learning-state.yaml`.
  2. Switch immediately to `references/coding-learning.md`.
  3. Extract the root mechanism from the real bug.
  4. Resume textbook progress only when the developer is ready.

---

## 3. Dynamic Knowledge Registry Evolution

The files under `knowledge/` must never be treated as a static, pre-packaged course library. The Knowledge Registry is an **evolving, self-expanding knowledge plane**:

```text
Local Textbooks (library/)  ──┐
Web Research (S0-S5)        ──┼──> Dynamic Knowledge Ingestion
Project Code (git diff)     ──┤       │
User Learning History       ──┘       ▼
                              Dynamic Mutation of
                             knowledge/**/*.yaml
                                      │
                                      ▼
                             Updated roadmap.yaml
```

### Ingestion Triggers
1. **On New Textbook Import**: When a local book is provided, the engine extracts previously unknown capabilities and writes new `.yaml` concept definitions into the appropriate domain directory.
2. **On Authoritative Gap Fill**: When web research discovers modern standards, it creates or updates the corresponding concept descriptor.
3. **On Misconception Detection**: When a user consistently exhibits a specific cognitive trap during checks, the engine appends the novel misconception to the target concept's `common_misconceptions` list.
