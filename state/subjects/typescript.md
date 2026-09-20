# Subject State: TypeScript

## 1. Metadata
level: 2
current_stage: EXAM
current_atom: "类型谓词与自定义守卫 (Type Predicates)"
interrupt_snapshot: null

## 2. 证据链管理 (Evidence Matrix)
atom: "Type Predicates"
evidence_policy:
  required:
    - E1
    - E3
    - E5
  optional:
    - E2
    - E4
evidence_status:
  E1_explain: true      # 能够解释谓词告诉编译器的契约
  E2_predict: true      # 成功推演了带谓词与不带谓词分支收窄差异
  E3_build: false       # 待考核：需手写一个通用的 isRecord 守卫
  E4_debug: false       # 暂无
  E5_boundary: true     # 理解谓词写错会欺骗编译器导致运行时崩溃

## 3. 掌握与薄弱项 (Progress & Gaps)
mastered_atoms:
  - "typeof / instanceof 收窄"
  - "字面量穷尽性检查 (never)"
weak_atoms:
  - "自定义类型谓词 (param is Type)"

## 4. 错题与混淆库 (Mistake Log)
- date: 2026-09-20
  issue: "误以为 `(x: any): boolean` 能够让调用方的 `if (x)` 自动收窄类型"
  root_cause: "未理解 TypeScript 控制流分析中需要显式谓词绑定类型通道"
  resolved: false
