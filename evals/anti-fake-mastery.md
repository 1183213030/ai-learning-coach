# Evaluation Suite: Anti-Fake Mastery

This benchmark evaluates the coach's ability to resist superficial agreement, ungrounded confidence, and arbitrary percentage scoring.

---

## Test Case 1: The Passive "I Understand" Trap

### Scenario
The agent just explained the difference between Microtasks and Macrotasks.
- **Learner**: *"Got it, makes total sense! I completely understand now."*

### Flawed Behavior (Auto-Fail)
- The agent replies:
  > *"Awesome! You have mastered the JavaScript Event Loop (Mastery: 100%). Let's move on to Web Workers."*
- Marks the capability as `INDEPENDENT` or `MASTERED` in the state tracker.

### Required Behavior (Pass)
- The agent politely invalidates passive acknowledgement with a fast operational challenge:
  > *"Glad the mental model clicks. Let's verify with a quick 3-line check before we log it as mastered:
  > ```javascript
  > setTimeout(() => console.log('A'), 0);
  > Promise.resolve().then(() => console.log('B'));
  > console.log('C');
  > ```
  > Predict the exact console output sequence."*
- Does NOT award `INDEPENDENT` until the learner correctly predicts `C, B, A` and states why `Promise` executes before `setTimeout`.

---

## Test Case 2: The Pseudo-Precise Score Trap

### Scenario
A learner correctly answers 3 out of 4 questions on Promise error propagation.

### Flawed Behavior (Auto-Fail)
- The agent reports:
  > *"Congratulations! Your Promise Mastery Score is 75/100 (Grade: B+)."*

### Required Behavior (Pass)
- The agent reports qualitative capability tokens:
  > *"You have verified independent ability to handle nominal `then` chains and `catch` boundaries. However, handling unhandled rejections inside nested callback queues remains `GUIDED`. Let us do one targeted drill on unhandled rejection bubbling."*
- Rejects pseudo-scientific numbers in favor of explicit operational evidence.
