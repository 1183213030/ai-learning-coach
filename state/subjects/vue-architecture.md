# Subject State: Vue 3 Architecture & Runtime

## 1. Metadata
level: 1
current_stage: INIT
current_atom: null
interrupt_snapshot: null

## 2. 知识体系树状图谱 (Curriculum & Skill Tree)

```
[Vue 3 核心原理与架构体系]
├── Module 1: 响应式系统内核 (Reactivity Engine)
│   ├── [ ] VUE-M1-A1: Proxy / Reflect 拦截机制与为何必须配合 Reflect
│   ├── [ ] VUE-M1-A2: 副作用函数 effect、依赖收集 (track) 与派发更新 (trigger)
│   ├── [ ] VUE-M1-A3: 分支切换与遗留依赖清理 (cleanup / bitwise flags)
│   ├── [ ] VUE-M1-A4: 嵌套 effect 与调度器 (scheduler) 工作原理
│   ├── [ ] VUE-M1-A5: computed 懒计算与脏检查标记 (dirty flag)
│   └── [ ] VUE-M1-A6: watch / watchEffect 调度机制与 flush (pre/post/sync)
├── Module 2: 渲染器与虚拟 DOM (Runtime Core & Diff)
│   ├── [ ] VUE-M2-A1: 虚拟节点 (VNode) 结构与 ShapeFlags 位掩码设计
│   ├── [ ] VUE-M2-A2: 挂载 (Mount) 与打补丁 (Patch) 核心流转过程
│   ├── [ ] VUE-M2-A3: Vue 2 双端 Diff 算法核心推演与边界场景
│   └── [ ] VUE-M2-A4: Vue 3 快速 Diff 算法（前置/后置预处理 + LIS 最长递增子序列移动算法）
├── Module 3: 编译器与编译期优化 (Compiler Core)
│   ├── [ ] VUE-M3-A1: 模板编译三阶段：Parse (AST) -> Transform -> Codegen
│   ├── [ ] VUE-M3-A2: 静态提升 (hoistStatic) 减少内存占用与 VNode 创建开销
│   ├── [ ] VUE-M3-A3: 补丁标志 (PatchFlags) 实现靶向动态节点更新
│   └── [ ] VUE-M3-A4: 动态节点收集与 Block Tree 拍平机制
└── Module 4: 组件生命周期与调度架构 (Component & Scheduler)
    ├── [ ] VUE-M4-A1: 组件实例初始化 (ComponentInstance) 与 setup 调用时机
    ├── [ ] VUE-M4-A2: 异步更新队列 (queueJob / queuePreFlushCb) 与 nextTick 微任务调度
    └── [ ] VUE-M4-A3: KeepAlive 缓存组件与 Teleport 底层 DOM 传送实现
```

## 3. 证据链管理 (Evidence Matrix)
atom: null
evidence_policy:
  required: [E1, E2, E3, E5]
  optional: [E4]
evidence_status:
  E1_explain: false
  E2_predict: false
  E3_build: false
  E4_debug: false
  E5_boundary: false

## 4. 掌握与艾宾浩斯复习调度 (Mastered Atoms & Spaced Review)
mastered_atoms: []
weak_atoms: []

## 5. 错题与混淆库 (Mistake Log)
