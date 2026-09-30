# Evaluation Suite: Coding Learning & AI Contribution Checks

This benchmark verifies that the coach correctly distinguishes AI-authored code from developer ability, properly extracts concepts from Git diffs, and grades code challenges strictly.

---

## Test Case 1: The AI-Generated Code Trap

### Scenario
The developer asks Antigravity to write a custom LRU Cache in TypeScript.
The AI agent writes a clean, optimal implementation using a `Map`.
The developer runs the tests, tests pass, and commits the code.

### Flawed Behavior (Auto-Fail)
- The coach records:
  > *"Capability: LRU Cache Implementation -> Status: INDEPENDENT (Verified by passing unit tests)."*

### Required Behavior (Pass)
- The coach records:
  > *"Task: LRU Cache Implementation. AI Contribution: L5 (100% AI-generated). Evidence: EXPOSED only."*
- Then, the coach prompts:
  > *"The AI wrote this LRU cache utilizing JavaScript's `Map` property order. To verify that you can build this without AI: why does `map.delete(key)` followed by `map.set(key, val)` refresh the eviction priority? Explain the V8 iteration mechanism."*

---

## Test Case 2: The Socratic Git Diff Intervention

### Scenario
The developer just finished refactoring an API client, replacing nested callbacks with `async/await` and an `AbortController`.
The developer types `/learn diff`.

### Required Behavior (Pass)
- The coach extracts the diff and detects the addition of `AbortController`.
- It filters out `async/await` because the developer already has `INDEPENDENT` evidence for basic async flows.
- It targets `AbortController` signal listening:
  > *"In `src/api/client.ts`, you added an `AbortSignal.timeout(5000)`. What happens if the server responds with headers within 4.9 seconds but body streaming takes 10 seconds? Will the request abort or complete?"*
- Binds directly to the developer's concrete codebase rather than an abstract textbook example.
