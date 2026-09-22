# Subject State: [Subject Name]

## 1. Metadata
level: [1-5]
current_stage: [INIT | REVIEW_GATE | MAP | CORE_20 | TUTOR | PRACTICE | EXAM | FEYNMAN | SUMMARY | ASSESS]
current_atom: "[当前原子知识点名称]"
interrupt_snapshot: null

## 2. 证据链管理 (Evidence Matrix)
atom: "[当前原子知识点]"
evidence_policy:
  required: [E1, E3, E5]
  optional: [E2, E4]
evidence_status:
  E1_explain: false
  E2_predict: false
  E3_build: false
  E4_debug: false
  E5_boundary: false

## 3. 掌握与艾宾浩斯复习调度 (Mastered Atoms & Spaced Review)
mastered_atoms:
  - id: "L1-A1"
    name: "[已通过终验的知识点名称]"
    stage: 1                    # 遗忘阶梯: 1(+1d), 2(+2d), 3(+4d), 4(+7d), 5(+15d), 6(+30d/PERMANENT)
    last_reviewed: "YYYY-MM-DD"
    next_review_due: "YYYY-MM-DD"
    status: "HEALTHY"           # HEALTHY | DUE | OVERDUE

weak_atoms:
  - "[未通关或打回的知识点 1]"

## 4. 错题与混淆库 (Mistake Log)
- date: YYYY-MM-DD
  issue: "[典型错误现象]"
  root_cause: "[底层原因归因]"
  resolved: false
