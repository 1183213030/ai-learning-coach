# Subject State: HTML5 Core & Web Standards

## 1. Metadata
level: 1
current_stage: TUTOR
current_atom: "HTML-M5-A3: 现代跨页面与实时网络通信 (postMessage / BroadcastChannel / SSE / WebSocket)"
interrupt_snapshot: null

## 2. 知识体系树状图谱 (全面整合企业级标准与全量特性)

```
[HTML5 核心标准与 Web 规范]
├── Module 1: 语义化结构、基础元素与无障碍 (Semantics & Elements) [✓ 全部通关]
│   ├── [✓] HTML-M1-A1: 语义化骨架标签 (Stage 3)
│   ├── [✓] HTML-M1-A2: 核心内容元素与嵌套规则 (Stage 2)
│   └── [✓] HTML-M1-A3: WAI-ARIA 规范与无障碍属性 (Stage 2)
├── Module 2: 文档解析、脚本加载与资源调度 (Parsing & Critical Path) [✓ 全部通关]
│   ├── [✓] HTML-M2-A1: HTML 词法解析、DOM 树构建与 iframe 沙箱 (sandbox) [Stage 2]
│   ├── [✓] HTML-M2-A2: script 标签加载策略 (async/defer/module) [Stage 2]
│   └── [✓] HTML-M2-A3: 关键资源提示符 (preload, prefetch, dns-prefetch) [Stage 2]
├── Module 3: 现代表单系统与约束验证 (Forms & Validation) [✓ 全部通关]
│   ├── [✓] HTML-M3-A1: 现代表单控件输入类型与属性 (required, pattern) [Stage 2]
│   └── [✓] HTML-M3-A2: 约束验证 API (validityState, checkValidity, setCustomValidity) [Stage 1]
├── Module 4: 多媒体、图形与交互 API (Media & Graphics) [业务专项: 后续结合项目]
└── Module 5: 客户端存储、并发与通信 (Storage & Advanced APIs) [当前收官冲刺]
    ├── [✓] HTML-M5-A1: 客户端 4 大存储机制 (Cookie / localStorage / sessionStorage / IndexedDB) [Stage 1]
    ├── [✓] HTML-M5-A2: Web Workers 多线程后台并发计算与数据传输 [Stage 1: 新入库]
    └── [CURRENT] HTML-M5-A3: 现代跨页面与实时网络通信 (postMessage / BroadcastChannel / SSE / WebSocket)
```

## 3. 证据链管理 (Evidence Matrix)
atom: "HTML-M5-A3: 现代跨页面与实时通信机制"
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
mastered_atoms:
  - id: "HTML-M1-A1"
    name: "语义化骨架标签"
    stage: 3
    last_reviewed: "2026-09-28"
    next_review_due: "2026-10-02"
    status: "HEALTHY"
  - id: "HTML-M1-A2"
    name: "核心内容元素与嵌套规则"
    stage: 2
    last_reviewed: "2026-09-28"
    next_review_due: "2026-09-30"
    status: "HEALTHY"
  - id: "HTML-M1-A3"
    name: "WAI-ARIA 规范与无障碍"
    stage: 2
    last_reviewed: "2026-09-28"
    next_review_due: "2026-09-30"
    status: "HEALTHY"
  - id: "HTML-M3-A1"
    name: "现代表单控件与原生校验属性 (required/pattern)"
    stage: 2
    last_reviewed: "2026-09-28"
    next_review_due: "2026-09-30"
    status: "HEALTHY"
  - id: "HTML-M3-A2"
    name: "约束验证 API"
    stage: 1
    last_reviewed: "2026-09-29"
    next_review_due: "2026-09-30"
    status: "HEALTHY"
  - id: "HTML-M2-A2"
    name: "script 加载策略 (async/defer/module)"
    stage: 2
    last_reviewed: "2026-09-29"
    next_review_due: "2026-10-01"
    status: "HEALTHY"
  - id: "HTML-M2-A3"
    name: "关键资源提示符 (preload/prefetch)"
    stage: 2
    last_reviewed: "2026-09-29"
    next_review_due: "2026-10-01"
    status: "HEALTHY"
  - id: "HTML-M2-A1"
    name: "HTML 词法解析、DOM 构建与 iframe sandbox"
    stage: 2
    last_reviewed: "2026-09-29"
    next_review_due: "2026-10-01"
    status: "HEALTHY"
  - id: "HTML-M5-A1"
    name: "客户端 4 大存储体系 (Cookie/Storage/IndexedDB)"
    stage: 1
    last_reviewed: "2026-09-29"
    next_review_due: "2026-09-30"
    status: "HEALTHY"
  - id: "HTML-M5-A2"
    name: "Web Workers 多线程后台计算"
    stage: 1
    last_reviewed: "2026-09-29"
    next_review_due: "2026-09-30"
    status: "HEALTHY"

weak_atoms: []

## 5. 错题与混淆库 (Mistake Log)
