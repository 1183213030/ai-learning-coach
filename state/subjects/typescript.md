# Subject State: TypeScript Static Type System

## 1. Metadata
level: 2
current_stage: EXAM
current_atom: "TS-M1-A3: 类型谓词与自定义守卫 (Type Predicates)"
interrupt_snapshot: null

## 2. 知识体系树状图谱 (Curriculum & Skill Tree)

```
[TypeScript 静态类型系统]
├── Module 1: 类型收窄与控制流分析 (Narrowing & Control Flow)
│   ├── [✓] TS-M1-A1: typeof / instanceof / in 操作符收窄
│   ├── [✓] TS-M1-A2: 判别式联合 (Discriminated Unions) 与 never 穷尽性检查
│   └── [CURRENT] TS-M1-A3: 自定义类型谓词 (param is Type) 与守卫封装
├── Module 2: 泛型编程与类型运算 (Generics & Type Operators)
│   ├── [ ] TS-M2-A1: 泛型约束 (extends) 与多类型参数推导
│   ├── [ ] TS-M2-A2: keyof, typeof 与索引访问类型 (T[K])
│   └── [ ] TS-M2-A3: 常量断言 (as const) 与只读元组类型推导
├── Module 3: 条件类型与模式匹配 (Conditional Types & Infer)
│   ├── [ ] TS-M3-A1: 条件类型语法 (T extends U ? X : Y) 与分布式特性 (Distributive)
│   ├── [ ] TS-M3-A2: infer 关键字与函数返回值/Promise 解包模式匹配
│   └── [ ] TS-M3-A3: 递归条件类型与深层只读/展开 (DeepReadonly)
└── Module 4: 映射类型与类型体操实战 (Mapped Types & Gymnastics)
    ├── [ ] TS-M4-A1: 映射类型修饰符 (+/- readonly, +/- ?)
    ├── [ ] TS-M4-A2: 模板字面量类型 (Template Literal Types) 与字符串重映射 (as)
    └── [ ] TS-M4-A3: 手写核心内置工具类型 (Partial, Required, Pick, Omit, Record, ReturnType)
```

## 3. 证据链管理 (Evidence Matrix)
atom: "Type Predicates"
evidence_policy:
  required: [E1, E3, E5]
  optional: [E2, E4]
evidence_status:
  E1_explain: true
  E2_predict: true
  E3_build: false
  E4_debug: false
  E5_boundary: true

## 4. 掌握与艾宾浩斯复习调度 (Mastered Atoms & Spaced Review)
mastered_atoms:
  - id: "TS-M1-A1"
    name: "typeof / instanceof 收窄"
    stage: 2
    last_reviewed: "2026-09-20"
    next_review_due: "2026-09-23"
    status: "DUE"
  - id: "TS-M1-A2"
    name: "字面量穷尽性检查 (never)"
    stage: 1
    last_reviewed: "2026-09-21"
    next_review_due: "2026-09-23"
    status: "DUE"

weak_atoms:
  - "自定义类型谓词 (param is Type)"

## 5. 错题与混淆库 (Mistake Log)
- date: 2026-09-20
  issue: "误以为 `(x: any): boolean` 能够让调用方的 `if (x)` 自动收窄类型"
  root_cause: "未理解 TypeScript 控制流分析中需要显式谓词绑定类型通道"
  resolved: false
