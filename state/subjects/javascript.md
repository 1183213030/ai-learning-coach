# Subject State: JavaScript

## 1. Metadata
level: 1
current_stage: TUTOR
current_atom: "执行上下文、词法作用域与闭包本质"
interrupt_snapshot: null

## 2. 证据链管理 (Evidence Matrix)
atom: "执行上下文、词法作用域与闭包本质"
evidence_policy:
  required: [E1, E2, E3, E5]
  optional: [E4]
evidence_status:
  E1_explain: false
  E2_predict: false
  E3_build: false
  E4_debug: false
  E5_boundary: false

## 3. 掌握与薄弱项 (Progress & Gaps)
mastered_atoms: []
weak_atoms:
  - "Event Loop 微任务与宏任务调度执行序"
  - "var 与 let 作用域机制及循环闭包引用捕获"
  - "CSS content-box 与 border-box 盒模型精确计算"

## 4. 错题与混淆库 (Mistake Log)
- date: 2026-09-21
  issue: "Promise 构造函数内部误认为异步延迟执行，未建立微任务优先清空模型"
  root_cause: "缺乏对 JavaScript 调用栈与任务队列底层交互的直观认知"
  resolved: false
- date: 2026-09-21
  issue: "for 循环中使用 var 时误认为每次迭代有独立作用域变量"
  root_cause: "混淆了函数作用域与块级作用域，忽视了闭包通过引用而非值捕获外层变量"
  resolved: false
- date: 2026-09-21
  issue: "content-box 物理总宽度计算遗漏 border 边框尺寸"
  root_cause: "盒模型几何结构概念记忆模糊"
  resolved: false
