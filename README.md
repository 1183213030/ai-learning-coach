<div align="center">

# AI Learning Coach (V3.0)

### 个人专属的知识驱动、概念边界展开与证据验收型技术学习操作系统 (Personal Learning OS)

让用户只需要会学习，剩下的交给 AI Learning Coach。

[![Protocol Version](https://img.shields.io/badge/Protocol-v3.0.0-007ACC?style=flat-square)](#)
[![Pedagogy](https://img.shields.io/badge/Pedagogy-Minimal%20Complete%20Coverage-4EBA6F?style=flat-square)](#)
[![Interaction](https://img.shields.io/badge/Interaction-Zero--Command%20Natural%20Language-orange?style=flat-square)](#)
[![Verification](https://img.shields.io/badge/Verification-Type--Specific%20Evidence-blueviolet?style=flat-square)](#)
[![License](https://img.shields.io/badge/License-MIT-lightgrey?style=flat-square)](#)

[简体中文](README.md) • [English](README_en.md)

</div>

---

## 核心突破：什么是真正的“教完整”？

传统 AI 教学最大的弊端在于：**只给一个抽象定义 + 一个简单的正确示例**。
学习者当时看懂了，但一旦遇到真实代码中形形色色的变体和陷阱，立刻陷入盲区。

**AI Learning Coach V3.0** 确立了一个全新的教学核心法典：
> **不是单纯“解释知识点”，而是穷举知识点的“可观察行为边界空间 (Minimal Complete Coverage)”。**

学习一个概念（如 `assertIn`、`Array.prototype.includes` 或 JavaScript 的 `==`），绝不仅仅是背下“它用于判断是否包含/是否相等”。系统会带你完整推演它的 **7 维行为空间**：
1. **核心不变量**：决定真伪的唯一底层物理规则；
2. **正向基准用例**：最干净、无干扰的标准成立场景；
3. **结构形变用例**：前后加上前缀、后缀、嵌套，验证为什么它*依然成立*；
4. **反例震撼冲击 (关键教学步)**：看起来极其相似，却*瞬间失败*的典型陷阱（例如 `admmmmmin` 不包含 `admin`，或 `['1'].includes(1)` 为假），逼迫大脑自己推导并锁定不变量；
5. **极值边界测试**：空值、特殊类型转换、`NaN`、引用对象等极端边缘情况；
6. **易混概念横向对比**：与生态中相似方法（如 `indexOf` vs `includes` vs `some`，或 `==` vs `===` vs `Object.is`）的同台辩论；
7. **真实工程锚点**：它在生产环境（如鉴权令牌解析、性能渲染拦截）中如何引发致命的隐蔽 Bug。

---

## 三大完整性原则 (Three Dimensions of Completeness)

系统围绕三个不可分割的完整性闭环运行：

| 维度 | 核心诉求 | 系统实现方式 |
| :--- | :--- | :--- |
| **1. 知识完整** | 搞透这个技术到底管哪些情况 | **概念边界展开引擎 (Concept Boundary Engine)**：正例、变式、反例、边界极值、相邻辨析。 |
| **2. 教学完整** | 怎么把一个小白真正带入门 | **震荡推演循环 (Shock & Deduce)**：先生活直觉、再代码观察、反例冲击后总结规律、最后才引入正式规范术语。 |
| **3. 能力完整** | 怎么证明学习者真的独立掌握了 | **分领域闭卷证据链 (Evidence Engine)**：关掉提示 (`L0`)，按知识类型分别考核时序推演、边界矩阵或手写重构，杜绝口头假懂。 |

---

## 极简交互体验：说人话即可

你不需要记忆任何命令，随时像在微信里与一位顶级技术导师对话：

```text
┌────────────────────────────────────────────────────────┐
│                                                        │
│  “我想系统学前端开发”                                 │
│  “我想系统搞懂 JavaScript 异步并发控制，我只会 async”  │
│  -> 开启新领域 (自动摸底诊断，按前置依赖循序渐进)       │
│                                                        │
│  “我完全不懂闭包，从零教我”                            │
│  “你刚才讲的太抽象了，换个生活比喻讲讲”                │
│  -> 启动小白模式 (生活直觉 -> 最小代码 -> 反例冲击)    │
│                                                        │
│  “继续昨天的学习”                                      │
│  “今天加班很累，只有10分钟，简单学一下”                │
│  -> 状态与时间自适应 (用户现实状态高于死板课程大纲)    │
│                                                        │
│  “考考我刚才学的，但不要给我任何提示”                  │
│  “先不学教材了，我工作里遇到了一个跨域报错”            │
│  -> 闭卷真实能力核验 (L0)，或就地取材解决生产 Bug      │
│                                                        │
└────────────────────────────────────────────────────────┘
```

---

## 三大中枢引擎架构

```text
                           AI Learning OS
                                  │
         ┌────────────────────────┼────────────────────────┐
         ▼                        ▼                        ▼
  Knowledge Engine         Teaching Engine          Evidence Engine
(概念边界展开与技能图谱)      (震荡教学与自适应引导)    (分领域闭卷能力审计)
         │                        │                        │
         ▼                        ▼                        ▼
Minimal Complete Coverage    Shock & Deduce Cycle     Type-Specific Proof
(7维行为边界空间)          (直觉-观察-反例-机制-工程) (不可伪造的 L0 证据底账)
         │                        │                        │
         └────────────────────────┼────────────────────────┘
                                  ▼
                         Learner State & Graph
                         (用户现实状态 > 课程大纲)
                                  │
                                  ▼
                       Review & Spaced Retention
                         (可逆退化动态复习防衰减)
```

---

## 快速上手与多 Agent 生态适配

### Google Antigravity
本仓库结构原生适配 Antigravity。在工作区对话框中直接输入任意自然语言即可开启学习。

### Claude Code
```bash
# 全局安装 (所有工程通用)
npx skills add https://github.com/1183213030/ai-learning-coach.git --skill ai-learning-coach --global --agent claude-code

# 或单项目安装
npx skills add https://github.com/1183213030/ai-learning-coach.git --skill ai-learning-coach --agent claude-code
```

### OpenAI Codex
```bash
npx skills add https://github.com/1183213030/ai-learning-coach.git --skill ai-learning-coach --global --agent codex
```

---

## 工程目录结构

```text
ai-learning-coach/
├── SKILL.md                          # V3.0 三大中枢核心协议规范
├── README.md                         # 简体中文主文档
├── README_en.md                      # English Documentation
│
├── knowledge/                        # 动态演化知识注册中心 (含 7 维行为边界展开)
│   ├── frontend/javascript/          # closure.yaml, scope.yaml, includes.yaml, equality.yaml
│   └── software-testing/             # test-case.yaml, unit-test.yaml
│
├── library/                          # 本地教材库 (Local-First 优先检索物理载体)
│   ├── frontend/                     # 前端工程体系教材
│   └── software-testing/             # 软件测试教材与案例
│
├── references/                       # 核心执行规范与调度策略 (Progressive Disclosure)
│   ├── concept-boundary-engine.md    # [V3.0 核心] 概念边界展开与最小完备覆盖规范
│   ├── teaching-protocol.md          # 老师人格、四级策略突变矩阵与微型行为探针
│   ├── curriculum-engine.md          # 现实状态优先调度、拓扑依赖寻路与单课生长
│   ├── intent-router.md              # 零命令自然语言意图分流与 Teach-vs-Check 隔离规范
│   ├── local-library.md              # 本地教材逆向解析与教材锚定教学协议
│   ├── knowledge-discovery.md        # 三源汇聚与 S0~S5 权威分级标准
│   ├── evidence-model.md             # E1~E5 证据矩阵与解耦评估模型
│   ├── learning-loop.md              # 10 步技术能力内化闭环 (Coding Learning Loop)
│   ├── coding-learning.md            # Git Diff 变更检测与真实工程探索
│   ├── socratic-hints.md             # L1~L5 渐进式启发阶梯
│   ├── review-system.md              # 遗忘抗衰减算法与动态退化逻辑
│   └── quality-rubric.md             # 严苛定性评分标准
│
└── templates/                        # 状态底账与记忆持久化模板
    ├── concept-expansion.yaml        # [V3.0 核心] 标准化 7 维概念展开模板
    ├── source-manifest.yaml          # 课程与知识点权威溯源清单
    ├── roadmap.yaml                  # 领域知识依赖拓扑图谱
    ├── curriculum-lesson.md          # 动态单课运行时生成模板
    ├── learner-profile.md            # 学习者全局画像与已知盲区
    ├── learning-state.yaml           # 当前学习焦点与复习队列
    ├── session.md                    # 单次会话流水日志
    └── evidence.yaml                 # 不可篡改的独立能力证据底账
```

---

## 许可证

本项目遵循 [MIT License](LICENSE) 开源协议。
