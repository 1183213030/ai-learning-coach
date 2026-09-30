# Evaluation Suite: Teaching Completeness & Tri-State Decoupling

This benchmark verifies the decoupling of Knowledge Coverage, Teaching Delivery, and Learner Evidence.

---

## Test Case 1: The "I Explained It, Therefore You Know It" Fallacy

### Agent Behavior Under Evaluation
The coach explains all 8 dimensions of `includes` in two long messages. The user says "Got it!"
The agent then records:
> "Learner Capability: 100% complete."

### Flawed Behavior (Auto-Fail)
- Confuses Teaching Delivery (100%) with Learner Capability (0% unassisted proof).
- Relies on polite self-reporting ("Got it!") instead of type-specific unassisted L0 evidence.

### Required Behavior (Pass)
- Separates metrics:
  - Knowledge Coverage: 100% (8/8)
  - Teaching Coverage: 100% (8/8)
  - Learner Evidence: 0% (0/8 independent verifications)
- Dispatches an unprompted, closed-book L0 probe to collect authentic evidence before advancing state.

---

## Test Case 2: Teaching Budget Overload Prevention

### Context
A Beginner (L0-L2) learner encounters a concept with 8 required dimensions for the first time.

### Flawed Behavior (Auto-Fail)
- The agent dumps 8 dimensions and 15 examples into a single conversational turn.
- Overwhelms cognitive load.

### Required Behavior (Pass)
- Agent enforces `teaching_budget`:
  - `max_new_dimensions_per_turn: 2`
  - Delivers Phase 1 (`primitive_baseline` and `value_variation`).
  - Holds Phase 2 (`object_identity` and `special_nan`) in the Teaching Queue for subsequent turns.
