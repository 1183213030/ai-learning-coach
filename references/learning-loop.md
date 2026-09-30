# The 10-Step Coding Learning Loop

This document specifies the operational execution of the 10-step learning loop for programming capabilities. Use this when facilitating deep learning sessions, project onboarding, or concept mastery.

---

## The Loop Flowchart

```text
1. CHANGE
   |
   v
2. OBSERVE
   |
   v
3. EXPLAIN
   |
   v
4. TRACE
   |
   v
5. TERMINOLOGY
   |
   v
6. PREDICT
   |
   v
7. MODIFY
   |
   v
8. IMPLEMENT
   |
   v
9. TRANSFER
   |
   v
10. REVIEW
```

---

## Detailed Step Protocols

### Step 1: CHANGE (Identification)
- **Objective**: Pinpoint the precise code delta or concept boundary.
- **Rules**:
  - Prefer real Git diffs, recent refactorings, or specific pull requests.
  - If no recent diff exists, isolate a minimal reproducible example (MRE) of 10-25 lines.
  - Never introduce more than one high-leverage architectural concept per iteration.

### Step 2: OBSERVE (Inspection before Explanation)
- **Objective**: Force active observation before any AI explanation.
- **Coach Action**: Show the code delta to the learner.
- **Prompt Example**:
  > "Take a look at lines 14-22 in the auth middleware. Before I explain why this change was made, what do you notice about how the token is handled after line 18?"

### Step 3: EXPLAIN (Mechanism Elicitation)
- **Objective**: Require the learner to verbalize the problem and solution.
- **Coach Action**: Solicit answers to four fundamental questions:
  1. What actually changed?
  2. What latent bug or bottleneck does this change resolve?
  3. What would break at runtime if we reverted this commit?
  4. What assumptions does this new approach make about inputs or external state?

### Step 4: TRACE (Execution & Data Flow Step-Through)
- **Objective**: Build an accurate mental runtime model.
- **Coach Action**: Ask the learner to step through execution step-by-step:
  - Call stack progression.
  - Microtask / macrotask queuing.
  - Memory references and garbage collection boundaries.
  - Side effects on shared or global state.

### Step 5: TERMINOLOGY (Anchor Concepts to Plain Language)
- **Objective**: Prevent empty buzzword memorization.
- **Coach Action**: For every critical term encountered (e.g. "Idempotence", "Lexical Closure", "Backpressure"):
  - **Plain-language definition**: What is the everyday intuition?
  - **Engineering definition**: What is the rigorous operational specification?
  - **Project context**: Where does this exact concept appear in the current codebase?
  - **Misconception check**: What is the common trap or incorrect belief?

### Step 6: PREDICT (Hypothesis & Failure Case Testing)
- **Objective**: Test the predictive power of the learner's mental model.
- **Coach Action**: Present a scenario with modified inputs or edge cases.
- **Prompt Example**:
  > "If the network drops while `refreshToken()` is in flight and two concurrent API calls arrive simultaneously, what will `authQueue` contain after 500ms? Predict the exact sequence before we run it."

### Step 7: MODIFY (Constraint Adaptation)
- **Objective**: Verify ability to adjust existing code under guidance.
- **Coach Action**: Introduce a new functional constraint or boundary condition.
- **Guidance**: Require the learner to edit 2 to 5 lines of the real code.
- **Evaluation**: Mark as `GUIDED` if hints are needed; check for regression in existing features.

### Step 8: IMPLEMENT (Zero-Scaffolding Reconstruction)
- **Objective**: Prove independent implementation capability (`L0`).
- **Coach Action**: Provide a blank slate or clean test file.
- **Requirements**:
  - The learner must write the core mechanism without copy-pasting AI code.
  - The AI must NOT supply boilerplate that solves the core algorithmic or architectural problem.
  - Success here unlocks the `INDEPENDENT` evidence token.

### Step 9: TRANSFER (Domain & Context Masking)
- **Objective**: Prove that the capability is not context-bound.
- **Coach Action**: Present a problem in a completely different domain or technical stack.
- **Key Rule**: **Do not mention the name of the concept in the prompt.**
- **Example**: If teaching `debounce` in a search UI, the transfer challenge should ask how to handle rapid sensor telemetry updates in a Node.js logging service.

### Step 10: REVIEW (Spaced Retrieval Scheduling)
- **Objective**: Lock the capability into long-term memory.
- **Coach Action**:
  - Record the result in `evidence.yaml`.
  - Schedule retrieval: Day +1, Day +4, Day +14, Day +30.
  - Update `learning-state.yaml`.
