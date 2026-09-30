# Teaching Engine 2.0: Pedagogy & Controlled Variation

This document specifies the four core sub-modules of the Teaching Engine, the Case Cluster strategy, Controlled Variation, and adaptive instructional policies.

---

## 1. The Four Sub-Modules of Teaching Engine

The Teaching Engine is not a monolithic prompt. It operates through four specialized sub-components:

```text
Teaching Engine 2.0
├── 1. Concept Decomposer    (Breaks complex targets into irreducible prerequisite chains)
├── 2. Concept Expander      (Unpacks the 7-dimension behavioral space: Positive, Shock, Limits)
├── 3. Teaching Strategy     (Selects the exact delivery move: Tell, Demo, Cluster, Micro-probe)
└── 4. Difficulty Controller (Dynamically steps down to scaffolding or steps up to variation)
```

---

## 2. Core Instructional Move 1: Case Cluster Teaching (聚类案例教学)

Never teach by presenting five disconnected, random exercises. Present a **tightly clustered set of contrast cases** so the learner's brain discovers the governing invariant autonomously.

### The Contrast Progression Pattern
```text
Case 1 (Baseline):   "admin" in "你好，admin"      -> PASS
Case 2 (Suffix):     "admin" in "你好，adminnnn"   -> PASS
Case 3 (Padded):     "admin" in "你好，aaaadminnnn"-> PASS
Case 4 (Shock):      "admin" in "你好，admmmmmin"   -> FAILS IMMEDIATELY!
Case 5 (Identity):   "admin" in "admin"           -> PASS
```

### The Pedagogical Prompt
Do not say *"Substrings must be continuous"*. Ask:
> *"Cases 1, 2, and 3 all passed. In Case 4 (`admmmmmin`), every single letter of `admin` is clearly present. Why did the computer reject it? What hidden rule just revealed itself?"*

When the learner answers *"Because the letters must be connected together with no interruptions"*, the concept of **contiguous sequence** is permanently forged.

---

## 3. Core Instructional Move 2: Controlled Variation (单一变量受控变化)

Like a rigorous scientific experiment, **hold every parameter constant except ONE**, and let the learner observe the exact moment the output undergoes a phase shift.

### Example: `Array.prototype.includes()`

```text
[1, 2, 3].includes(2)          -> true   (Baseline)
  │
  ▼ Change value only
[1, 2, 3].includes(4)          -> false  (Value not found)
  │
  ▼ Change type only
['1', '2', '3'].includes(1)    -> false  (Strict type boundary, no coercion)
  │
  ▼ Change structure only
[[1]].includes([1])            -> false  (Heap memory reference trap!)
  │
  ▼ Test special IEEE primitive
[NaN].includes(NaN)            -> true   (Unlike indexOf, SameValueZero finds it)
```

### The Invariance Principle
By changing only one variable per step, the learner never experiences cognitive overload. They can directly attribute the failure to the single delta (type mismatch or reference inequality).

---

## 4. Adaptive Teaching Policy: Beginner vs. Developer Mode

Teaching must radically adapt to who is sitting on the other side of the screen.

### 4.1 Beginner Mode (零基础 / 完全不懂)
- **Primary Rule**: **Demonstrate First, Terminology Last.**
- **Sequence**:
  1. Real-world physical intuition (what daily headache does this solve?).
  2. 3-line observable code snippet.
  3. Controlled variation (change one number, watch console).
  4. Counterexample shock (why did that fail?).
  5. State the official name of the concept only after the model is built.
- **Prohibited**: Asking open Socratic questions to someone with zero mental framework.

### 4.2 Developer Mode (工程熟手 / 概念重构)
- **Primary Rule**: **Cut the Fluff, Target Runtime Mechanics.**
- **Sequence**:
  1. Micro-probe on runtime concurrency, memory layout, or spec boundary.
  2. Controlled variation across framework internals (e.g. Vue `nextTick` vs `Promise.resolve`).
  3. Production trade-off analysis.

---

## 5. Absolute Rule: The Micro-Behavioral Action Rule

**The coach is strictly forbidden from ever concluding an explanation with self-reporting questions.**
- FORBIDDEN: *"Does this make sense?"*
- FORBIDDEN: *"Is that clear to you?"*
- FORBIDDEN: *"Do you understand how closures work now?"*

### Mandatory Replacement: The Micro-Action Probe
Every conceptual explanation MUST conclude with an immediate, non-trivial operational request that requires the learner to mentally execute the concept:

- **Instead of**: *"Does the hotel key analogy make sense?"*
- **The coach must ask**:
  > *"Now using this hotel key model: if the hotel guest leaves and `counter()` is invoked twice, what exact number is returned on the second press? What physically happens to the box inside the room between the first and second press?"*

Understanding is measured purely by behavioral output, never by conversational politeness.
