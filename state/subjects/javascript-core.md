# Subject State: JavaScript Deep Core

## 1. Metadata
level: 1
current_stage: REVIEW_GATE
current_atom: "JS-M2-A3: async/await 状态机脱糖与调用栈时序"
interrupt_snapshot: null

## 2. 知识体系树状图谱 (Curriculum & Skill Tree)

```
[JavaScript 深度内核]
├── Module 1: 运行时、执行机制与内存模型 (Runtime & Memory)
│   ├── [✓] JS-M1-A1: 执行上下文 (EC)、变量对象 (VO/AO) 与词法作用域链
│   ├── [✓] JS-M1-A2: 闭包底层本质、堆内存逃逸分析与 GC 垃圾回收机制
│   └── [ ] JS-M1-A3: this 绑定四种规则、优先级与隐式丢失防御
├── Module 2: 异步并发与事件循环体系 (Async & Concurrency)
│   ├── [✓] JS-M2-A1: 调用栈与 Event Loop 调度模型（宏任务/微任务/渲染帧时序）
│   ├── [✓] JS-M2-A2: Promise 内部状态机模型与 microtask 绑定机制
│   └── [CURRENT] JS-M2-A3: async/await 协程脱糖机制与调用栈切入边界
├── Module 3: 原型系统与对象元编程 (Prototypes & Metaprogramming)
│   ├── [ ] JS-M3-A1: 原型链 `__proto__` 与 `prototype` 拓扑结构与 new 操作符底层白板推演
│   ├── [ ] JS-M3-A2: 属性描述符 (Property Descriptors) 与对象冻结/密封
│   └── [ ] JS-M3-A3: Proxy 代理与 Reflect 映射反射机制
└── Module 4: 模块化与工程边界 (Module System & Boundary)
    ├── [ ] JS-M4-A1: CommonJS 与 ES Module 底层加载机制、循环依赖与引用差异
    └── [ ] JS-M4-A2: 内存泄漏常见场景 (Detached DOM, Timers, Global Cache) 诊断
```

## 3. 证据链管理 (Evidence Matrix)
atom: "async/await 协程脱糖机制与调用栈切入边界"
evidence_policy:
  required: [E1, E2, E3, E5]
  optional: [E4]
evidence_status:
  E1_explain: true
  E2_predict: true
  E3_build: false
  E4_debug: false
  E5_boundary: false

## 4. 掌握与艾宾浩斯复习调度 (Mastered Atoms & Spaced Review)
mastered_atoms:
  - id: "JS-M1-A1"
    name: "执行上下文与作用域链"
    stage: 2
    last_reviewed: "2026-09-21"
    next_review_due: "2026-09-23"
    status: "DUE"
  - id: "JS-M1-A2"
    name: "闭包机制与内存GC"
    stage: 2
    last_reviewed: "2026-09-21"
    next_review_due: "2026-09-23"
    status: "DUE"
  - id: "JS-M2-A1"
    name: "事件循环三层调度"
    stage: 1
    last_reviewed: "2026-09-22"
    next_review_due: "2026-09-23"
    status: "DUE"

weak_atoms: []

## 5. 错题与混淆库 (Mistake Log)
