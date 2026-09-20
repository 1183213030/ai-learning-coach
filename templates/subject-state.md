# Subject State: [Subject Name]

## 1. Metadata
level: [1-5]
current_stage: [INIT | MAP | CORE_20 | TUTOR | PRACTICE | EXAM | FEYNMAN | SUMMARY | ASSESS]
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

## 3. 掌握与薄弱项 (Progress & Gaps)
mastered_atoms:
  - "[已通过终验的知识点 1]"
weak_atoms:
  - "[未通关或打回的知识点 1]"

## 4. 错题与混淆库 (Mistake Log)
- date: YYYY-MM-DD
  issue: "[典型错误现象]"
  root_cause: "[底层原因归因]"
  resolved: false
