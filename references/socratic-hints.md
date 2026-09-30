# The Socratic Hint Ladder (L1 to L5)

This document provides explicit dialogue patterns and operational rules for the progressive scaffolding ladder. Scaffolding must always descend step-by-step; never jump from L1 directly to L5.

---

## 1. The 5-Level Scaffolding Framework

```text
[ L1: Open Question ]        Prompts unguided reasoning.
         |
         v (if learner cannot answer or is stuck)
[ L2: Narrowing Hint ]       Directs gaze to a specific location or token.
         |
         v (if still stuck)
[ L3: Directional Hint ]     Identifies the operational mechanism or rule.
         |
         v (if still stuck)
[ L4: Partial Solution ]     Gives 50% of the answer / mental structure.
         |
         v (if still stuck)
[ L5: Full Explanation ]     Reveals the complete solution + forces immediate check.
```

---

## 2. Concrete Exemplar: JavaScript Closure & Event Loop

### Scenario
The learner is examining the classic async loop bug:
```javascript
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 100);
}
```

---

### Level 1: Open Question
- **Goal**: Check baseline mental model.
- **Coach**:
  > "Before running this in Node, what numbers do you expect to print to the console once the timers fire?"
- **Permitted Outcomes**:
  - If learner says: *"0, 1, 2"* -> Wrong prediction; proceed to Level 2.
  - If learner says: *"3, 3, 3 because `var` is function-scoped"* -> Correct prediction + mechanism; advance to `E4: Implement` with a custom block scope.

---

### Level 2: Narrowing Hint
- **Goal**: Direct focus to the variable declaration and scope lifetime.
- **Coach**:
  > "Look specifically at the keyword declaring `i` on line 1, and think about when the callbacks inside `setTimeout` actually execute relative to when the loop finishes."
- **Permitted Outcomes**:
  - Learner recognizes the timing difference -> Proceed to elicit mechanism.
  - Learner still puzzled -> Proceed to Level 3.

---

### Level 3: Directional Hint
- **Goal**: State the governing principle without giving the answer.
- **Coach**:
  > "Remember that `var` creates a single variable bound to the enclosing function scope, not the for-loop block. By the time the JavaScript event loop executes the timer callbacks 100ms later, what has happened to that single `i` variable?"
- **Permitted Outcomes**:
  - Learner answers: *"The loop has already finished, so `i` is 3!"* -> Success at `L3` (`GUIDED` evidence recorded).

---

### Level 4: Partial Solution
- **Goal**: Provide the structural skeleton; learner completes the binding.
- **Coach**:
  > "Because there is only one shared `i`, all three callbacks reference that same memory slot at the end. To fix this without `let`, we need an IIFE (Immediately Invoked Function Expression) to capture `i` in a separate lexical scope per iteration. Here is the outer skeleton:
  > ```javascript
  > for (var i = 0; i < 3; i++) {
  >   ((capturedIndex) => {
  >     // TODO: Place the setTimeout here
  >   })(i);
  > }
  > ```
  > Complete lines 3-4 so each callback logs its own captured index."

---

### Level 5: Full Explanation + Immediate Forced Verification
- **Goal**: Complete explanation; mandatory immediate follow-up task.
- **Coach**:
  > "Here is the complete solution and explanation:
  > ```javascript
  > for (var i = 0; i < 3; i++) {
  >   setTimeout(((val) => () => console.log(val))(i), 100);
  > }
  > ```
  > **Mechanism**: The outer function executes immediately during the loop tick, binding `i` to `val` in that unique closure. When the inner function runs 100ms later, it reads its own immutable lexical environment.
  >
  > **Mandatory Verification**: Now, without using an IIFE or `setTimeout`, write a function `makeAdder(x)` that returns a function adding `x` to an argument `y`. Run it twice with different initial values."
