# Subject State: Frontend Job-Hunting Practical Roadmap (前端上岸四阶实战路线)

## 1. Metadata
level: 1
current_stage: PRACTICE
current_atom: "Stage 1 - 基础页面布局、接口联调与异常空状态兜底"
interrupt_snapshot: null

## 2. 路线进度与 13 步考点映射 (Curriculum Progress)
- [ ] **阶段 ①：基础页面开发 + 接口联调** (含: HTML/CSS, JS基础, DOM事件委托, HTTP联调, 响应式) — 对应配图 第1/2/3/5/12步
- [ ] **阶段 ②：框架核心 + 状态与类型** (含: Vue/React核心机制, 组件通信, 状态管理, TypeScript) — 对应配图 第6/8/9步
- [ ] **阶段 ③：工程化 + 手撕代码 + 原理** (含: Vite/Webpack, 防抖节流/深拷贝/异步并发, 闭包/原型链/宏微任务) — 对应配图 第2/4/7步深化
- [ ] **阶段 ④：性能优化 + 线上排障 + 项目复盘** (含: 浏览器渲染/内存泄漏, 首屏/缓存策略, XSS/CSRF安全, 项目复盘) — 对应配图 第4/10/11/13步

## 3. 当前原子证据链 (Evidence Matrix)
atom: "接口联调与异常边界处理 (空数据/报错兜底)"
evidence_policy:
  required: [E1, E3, E5]
  optional: [E2, E4]
evidence_status:
  E1_explain: false   # 解释 HTTP 状态码、跨域及异步请求状态流转
  E2_predict: false   # 预测异步请求并发或异常时的执行顺序
  E3_build: false     # 独立写出含 Loading/Empty/Error 兜底的列表渲染与接口对接代码
  E4_debug: false     # 修复接口报错未捕获或死循环请求问题
  E5_boundary: false  # 清楚数据为空、字段缺失、网络断开时的防御性写法

## 4. 已掌握原子与复习调度 (Mastered Atoms & Spaced Review)
mastered_atoms: []
weak_atoms: []

## 5. 简历亮点话术库 (Resume Highlight Bank)
- (待阶段①完成后按 STAR 法则沉淀，如: "基于原生事件委托与 AbortController 封装高可用列表请求模块，解决高频切换竞态与空状态白屏问题")
