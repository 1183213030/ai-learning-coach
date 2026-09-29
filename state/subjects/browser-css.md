# Subject State: Browser Rendering & Modern CSS

## 1. Metadata
level: 1
current_stage: INIT
current_atom: null
interrupt_snapshot: null

## 2. 知识体系树状图谱 (Curriculum & Skill Tree)

```
[现代 Web 渲染与 CSS 工程]
├── Module 1: 盒模型几何计算与视觉格式化上下文 (Box Model & Formatting)
│   ├── [✓] CSS-M1-A1: content-box 与 border-box 物理总宽高几何计算公式
│   ├── [ ] CSS-M1-A2: 块级格式化上下文 (BFC) 触发条件、高度塌陷与外边距折叠消除
│   └── [ ] CSS-M1-A3: 层叠上下文 (Stacking Context) 与 z-index 空间层级裁决规则
├── Module 2: 现代排版布局算法 (Modern Layout Engines)
│   ├── [✓] CSS-M2-A1: Flexbox 轴线系统 (Main/Cross Axis) 与对齐属性工程化
│   ├── [ ] CSS-M2-A2: Flex 弹性伸缩算法 (flex-grow, flex-shrink, flex-basis) 剩余空间分配
│   └── [ ] CSS-M2-A3: CSS Grid 网格布局、自适应轨迹 (fr, minmax, auto-fill) 与区域模板
└── Module 3: 浏览器渲染管线与性能优化 (Rendering Pipeline & Performance)
    ├── [ ] CSS-M3-A1: 渲染管线 5 大阶段 (DOM + CSSOM -> Render Tree -> Layout -> Paint -> Composite)
    ├── [ ] CSS-M3-A2: 重排 (Reflow / Layout) 与重绘 (Repaint) 的触发源与代价优化
    └── [ ] CSS-M3-A3: 合成层 (Compositing Layers)、GPU 硬件加速与 will-change 边界
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
mastered_atoms:
  - id: "CSS-M1-A1"
    name: "content-box 与 border-box 几何计算"
    stage: 2
    last_reviewed: "2026-09-21"
    next_review_due: "2026-09-23"
    status: "DUE"
  - id: "CSS-M2-A1"
    name: "Flexbox 轴线对齐与居中"
    stage: 1
    last_reviewed: "2026-09-22"
    next_review_due: "2026-09-23"
    status: "DUE"

weak_atoms: []

## 5. 错题与混淆库 (Mistake Log)
- date: 2026-09-21
  issue: "content-box 物理总宽度计算遗漏 border 边框尺寸"
  root_cause: "已通过 border-box 实战计算完全修复"
  resolved: true
