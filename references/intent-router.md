# Intent Router & Natural Language Ingress

This document specifies how natural user dialogue is parsed and routed to internal learning operations without forcing the user to memorize command flags.

---

## 1. The Zero-Command Interaction Philosophy

The user should not be burdened with system administration commands. The interface exposes three high-level conversational modalities:

```text
                               User Input
                                   │
             ┌─────────────────────┼─────────────────────┐
             ↓                     ↓                     ↓
       "我想学 [X]"            "继续学习"             "具体提问 / 代码"
     (New Journey)            (Resume Focus)        (Targeted Query)
             │                     │                     │
             └─────────────────────┼─────────────────────┘
                                   ↓
                       Internal Intent Router
                                   │
    ┌──────────┬──────────┬────────┴─┬──────────┬──────────┬──────────┐
    ↓          ↓          ↓          ↓          ↓          ↓          ↓
  START     CONTINUE    TEACH      CHECK      SEARCH      DIFF     REVIEW
```

---

## 2. Intent Classification Matrix

The coach classifies incoming messages into one of the following internal intents:

| Natural Language Triggers | Classified Intent | Internal Sub-Flow Executed |
| :--- | :--- | :--- |
| *"我想系统学软件测试"*, *"我要从零开始学前端"* | `START_DOMAIN` | 1. Check local `library/` -> 2. Run light diagnostic -> 3. Build `roadmap.yaml` -> 4. Deliver Lesson 1. |
| *"继续学"*, *"继续昨天的进度"*, `/learn` | `CONTINUE` | 1. Read `learning-state.yaml` -> 2. Identify unverified task from `session.md` -> 3. Resume immediately. |
| *"给我讲讲闭包"*, *"从基础教我这个概念"* | `TEACH_CONCEPT` | Execute `references/teaching-protocol.md`: Prediction -> MCE explanation -> Socratic ladder. |
| *"考考我闭包"*, *"做个练习验证我掌握了没"* | `CHECK_CAPABILITY`| Execute strict Check protocol: 3-part verification (Predict, Modify, Implement) -> Log to `evidence.yaml`. |
| *"为什么这里要用 computed 而不是 watch?"* | `WHY_DECISION` | Execute 7-element trade-off chain (Context, Problem, Constraint, Mechanism, Consequence, Alt, Trade-off). |
| *"看下我刚才改的代码"*, `/learn diff` | `PROJECT_DIFF` | Inspect `git diff` -> Detect new pattern -> Trigger single high-leverage challenge. |
| *"帮我复习一下之前的"*, *"我感觉快忘了 Promise"* | `REVIEW_DUE` | Inspect `due_reviews` queue -> Run blind retrieval challenge -> Update retention state. |
| *"我最近到底学会了什么"*, *"做个学习总结"* | `RECAP_AUDIT` | Audit `evidence.yaml` -> Group verified `L0` capabilities vs. unverified `EXPOSED` items. |

---

## 3. The `TEACH` vs. `CHECK` Separation Mandate

A core design rule of V2.1: **Teaching and Checking must NEVER occur in the same conversational turn.**

```text
[ TEACH TURN ]
  1. Present counter-intuitive puzzle or observable behavior.
  2. Ask for prediction.
  3. Deliver Minimal Sufficient Explanation (MCE, under 200 words).
  4. Provide 1 illustrative code example (<15 lines).
  5. Guide understanding via Socratic hints (L1-L3).
  (STOP - Do NOT mark mastery here)

[ CHECK TURN ] (Initiated explicitly or as next step)
  1. Wipe chat context cues ("Without looking at our previous snippet...").
  2. Part A: Explain mechanism in own words without jargon.
  3. Part B: Trace runtime execution order under fresh inputs.
  4. Part C: Independent zero-scaffolding code implementation (L0).
  5. Record verified tokens (E1-E5) into evidence.yaml.
```
