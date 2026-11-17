# Subject State: 前端工程与面试通关 (Frontend Engineering & Interview Mastery)

## 1. Metadata
level: 3
current_stage: EXAM
current_atom: "FE-L3-A1: 手写 Promise A+ 规范 (链式调用与值穿透)"
contract_ref: "knowledge/frontend/javascript/promise.yaml"
interrupt_snapshot: null

## 2. 能力阶梯与体系图谱 (Curriculum & 5-Level MAP)

```
[前端工程与面试通关 5-Level MAP]
├── Level 1: 菜鸟教程标准 (Syntax & API Semantics) [PASS 100% 全部通关]
│   ├── [PASS]    FE-L1-A1: JS 原始数据类型判定与 typeof 语义规范 (已掌握)
│   ├── [PASS]    FE-L1-A2: 数组核心原生方法返回值与就地变异边界 (已掌握)
│   ├── [PASS]    FE-L1-A3: CSS 标准盒模型与怪异盒模型尺寸计算法则 (已掌握)
│   └── [PASS]    FE-L1-A4: 基础选择器权重等级与继承特性 (已掌握)
├── Level 2: 大厂笔试真题 (Runtime Derivation & Protocols) [PASS 100% 全部通关]
│   ├── [PASS]    FE-L2-A1: 执行上下文 (EC)、词法作用域链与闭包捕获 (已掌握)
│   ├── [PASS]    FE-L2-A2: 事件循环与时序推演 (宏任务/微任务/Promise/微任务切入点) (已掌握)
│   ├── [PASS]    FE-L2-A3: 隐式强制类型转换与原型链拓扑推导 (已掌握)
│   └── [PASS]    FE-L2-A4: HTTP 状态码语义与浏览器强协商缓存策略 (已掌握)
├── Level 3: 核心机制与手写实战 (Hardcore Implementations) [ACTIVE]
│   ├── [RUNNING] FE-L3-A1: 手写 Promise A+ 规范 (链式调用与值穿透) (当前切入点)
│   ├── [QUEUED]  FE-L3-A2: 异步并发调度池 (Concurrency Pool) 熔断与恢复
│   ├── [QUEUED]  FE-L3-A3: 防抖 (Debounce) 与节流 (Throttle) 边界处理 (立即执行/取消/返回值)
│   └── [QUEUED]  FE-L3-A4: 高性能 DOM 事件委托与跨节点事件传播控制
├── Level 4: 现代框架与生态底层 (Framework Underpinnings)
│   ├── [ ] FE-L4-A1: Vue 3 响应式底层 (Proxy/Reflect 与依赖收集 Track/Trigger)
│   ├── [ ] FE-L4-A2: 虚拟 DOM 树比对与 Diff 算法核心演进 (双端对比 vs 快速 Diff)
│   └── [ ] FE-L4-A3: TypeScript 进阶类型体操 (条件类型、infer 模式匹配、分布式条件类型)
└── Level 5: 大厂面试与架构场景 (Engineering & System Architecture)
    ├── [ ] FE-L5-A1: 前端工程化构建链路 (Monorepo、Bundleless 模块热替换与分包策略)
    ├── [ ] FE-L5-A2: Web Vitals 核心性能指标归因与真实线上排障
    └── [ ] FE-L5-A3: 真实大规模业务场景架构设计 (大型表单状态流、离线化与微前端隔离)
```

## 3. 证据链管理 (Evidence Matrix)
atom: "FE-L3-A1: 手写 Promise A+ 规范 (链式调用与值穿透)"
contract_ref: "knowledge/frontend/javascript/promise.yaml"
evidence_policy:
  required: [E1, E2, E3, E4]
  optional: [E5]
evidence_status:
  E1_explain: false
  E2_predict: false
  E3_build: false
  E4_debug: false
  E5_boundary: false

## 4. 掌握与艾宾浩斯复习调度 (Mastered Atoms & Spaced Review)
mastered_atoms:
  - id: "FE-L1-A1"
    name: "JS 原始数据类型判定与 typeof 语义规范"
    stage: 2
    last_reviewed: "2026-10-10"
    next_review_due: "2026-10-12"
    status: "HEALTHY"
  - id: "FE-L1-A2"
    name: "数组核心原生方法返回值与就地变异边界"
    stage: 2
    last_reviewed: "2026-10-10"
    next_review_due: "2026-10-12"
    status: "HEALTHY"
  - id: "FE-L1-A3"
    name: "CSS 标准盒模型与怪异盒模型尺寸计算法则"
    stage: 1
    last_reviewed: "2026-10-10"
    next_review_due: "2026-10-11"
    status: "HEALTHY"
  - id: "FE-L1-A4"
    name: "基础选择器权重等级与继承特性"
    stage: 1
    last_reviewed: "2026-10-10"
    next_review_due: "2026-10-11"
    status: "HEALTHY"
  - id: "FE-L2-A1"
    name: "执行上下文 (EC)、词法作用域链与闭包捕获"
    stage: 1
    last_reviewed: "2026-10-10"
    next_review_due: "2026-10-11"
    status: "HEALTHY"
  - id: "FE-L2-A2"
    name: "事件循环与时序推演 (宏任务/微任务/Promise/微任务切入点)"
    stage: 1
    last_reviewed: "2026-10-10"
    next_review_due: "2026-10-11"
    status: "HEALTHY"
  - id: "FE-L2-A3"
    name: "隐式强制类型转换与原型链拓扑推导"
    stage: 1
    last_reviewed: "2026-10-10"
    next_review_due: "2026-10-11"
    status: "HEALTHY"
  - id: "FE-L2-A4"
    name: "HTTP 状态码语义与浏览器强协商缓存策略"
    stage: 1
    last_reviewed: "2026-10-10"
    next_review_due: "2026-10-11"
    status: "HEALTHY"

weak_atoms:
  - "FE-L3-A1: 手写 Promise A+ 规范 (链式调用与值穿透)"

## 5. 错题与混淆库 (Mistake Log)
- date: 2026-10-09
  issue: "误认为 typeof 返回类型缩写或特定名称 (如 str/null/arr)"
  root_cause: "未建立 typeof 固定返回值字符串枚举的物理心智；遗漏了 typeof null === 'object' 的规范定义以及 Array 在原型层属于 Object 的本质"
  resolved: false
- date: 2026-10-09
  issue: "未知如何准确区分对象与数组类型"
  root_cause: "缺失 ES5+ 静态方法 Array.isArray() 及 Object.prototype.toString.call 原型检测手段的认知储备"
  resolved: false
- date: 2026-10-09
  issue: "未知 NaN 的类型与自身非等性"
  root_cause: "缺失 IEEE 754 浮点数规范中 NaN 属于 number 类型以及唯一不自等特性的心智模型"
  resolved: true
- date: 2026-10-10
  issue: "误认为 Array.prototype.push() 返回变异后的数组"
  root_cause: "混淆了 API 的副作用与返回值语义，遗漏了 push() 返回值为最新 length (数字) 的规范定义"
  resolved: true
- date: 2026-10-10
  issue: "误认为 pop() 不改变原数组且返回值为数组长度"
  root_cause: "未建立栈结构 (push/pop) 对原数组的破坏性变异机制，遗漏了 pop() 返回值为被弹出元素本身的规范定义"
  resolved: true
- date: 2026-10-10
  issue: "误认为 slice() 会就地修改原数组"
  root_cause: "混淆了 slice (非破坏性纯函数切片) 与 splice (破坏性就地变异剪接) 的 API 边界"
  resolved: true
- date: 2026-10-10
  issue: "误认为 var 会销毁无法进入函数，且误以为换成 let 可以穿透读取外部变量"
  root_cause: "缺失执行上下文变量提升 (Hoisting)、作用域遮蔽 (Shadowing) 及 ES6 暂时性死区 (TDZ) 的规范认知"
  resolved: true
- date: 2026-10-10
  issue: "误认为 let 提升后会被初始化为 undefined"
  root_cause: "混淆了 var 的创建即初始化与 let/const 的创建与初始化解耦，未建立暂时性死区 (TDZ) 抛出 ReferenceError 的心智模型"
  resolved: true
- date: 2026-10-10
  issue: "误将作用域链向外查找的通用机制归因于 let 关键字特性"
  root_cause: "未完全理解无论 var 还是 let 均遵循词法作用域链逐级向上查找的通用规则"
  resolved: true
- date: 2026-10-10
  issue: "混淆 setTimeout (宏任务) 与 Promise.then (微任务) 的时序调度优先级"
  root_cause: "遗漏了事件循环在同步执行栈清空后必须先清空微任务队列、再拉取宏任务的调度法则"
  resolved: true
- date: 2026-10-10
  issue: "误认为 delete 自身属性后访问该属性返回 undefined"
  root_cause: "遗漏了 delete 仅作用于实例自身，以及属性在自身不存在时会沿着原型链向上回退查找的机制"
  resolved: true
- date: 2026-10-10
  issue: "误认为 Object.prototype.__proto__ 指向 Object"
  root_cause: "未理解原型链防止循环引用的终止条件，遗漏了规范定义 null 为原型链唯一终点的设计"
  resolved: true
- date: 2026-10-10
  issue: "未知协商缓存命中时的 HTTP 状态码与空响应体规范"
  root_cause: "缺失 HTTP 304 Not Modified 语义及 If-None-Match/ETag 报文交互协议储备"
  resolved: true
- date: 2026-10-10
  issue: "未知 Promise A+ 规范的三种状态枚举及状态不可逆流转法则"
  root_cause: "缺失 Promise 内部核心状态机 (pending/fulfilled/rejected) 及凝固态守卫机制的心智模型"
  resolved: false
















