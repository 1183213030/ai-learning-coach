<div align="center">

# AI Learning Coach

### 个人专属的知识驱动与证据验收型技术学习操作系统 (Personal Learning OS)

让用户只需要会学习，剩下的交给 AI Learning Coach。

[![Protocol Version](https://img.shields.io/badge/Protocol-v2.2.0-007ACC?style=flat-square)](#)
[![Interaction](https://img.shields.io/badge/Interaction-Zero--Command%20Natural%20Language-4EBA6F?style=flat-square)](#)
[![Verification](https://img.shields.io/badge/Verification-Type--Specific%20Evidence-orange?style=flat-square)](#)
[![Architecture](https://img.shields.io/badge/Architecture-Six--Tier%20Knowledge%20Plane-blueviolet?style=flat-square)](#)
[![License](https://img.shields.io/badge/License-MIT-lightgrey?style=flat-square)](#)

[简体中文](README.md) • [English](README_en.md)

</div>

---

## 项目概述

在大模型普及的今天，获取现成代码和答案变得前所未有的廉价，但**真正建立属于自己的技术工程能力却变得越来越难**。

### 传统 AI 学习的两大通病
1. **虚假胜任感 (The Illusion of Competence)**：阅读 AI 详尽的解释或复制 AI 生成的代码，让人误以为自己掌握了；但一旦脱离 AI 白纸盲打、分析复杂系统时序或排查线上事故时，瞬间束手无策。
2. **碎片化与无体系 (Fragmented & Ad-hoc)**：今天问一个配置，明天问一段报错，学到的全是零碎拼图，脑海里始终无法形成清晰完整的技术知识骨架。

**AI Learning Coach** 彻底颠覆了“你问我答”的传统问答模式与“机械播放章节”的死板网课模式。它将 AI 从被动的代码生成器，转变为**带有长期记忆、掌握客观证据、动态规划知识树并自适应学习者现实状态的随身技术教练**。

---

## 核心设计哲学

> **现实状态决定现在学什么，客观证据决定到底会不会。**

- **全局视野，告别碎片化**：无论你想掌握现代前端、JavaScript 内核还是其他技术领域，系统会首先构建清晰的**前置依赖技能树 (Roadmap)**，让你清楚看到起点、当前关卡与终点，一环扣一环扎实推进。
- **启发引导，拒绝填鸭灌输**：遇到不懂的原理，系统绝不倾倒长篇大论，而是通过生活隐喻、观察矛盾、小步预测，引导你自己推导出答案。
- **闭卷检验，彻底击碎假懂**：嘴上说“理解了”在系统里积分为零。系统严格将**教学 (Teach)** 与 **检验 (Check)** 分离。考核时关闭提示与答案泄露，唯有你独立完成白话阐述、时序预测或独立手写，才算真正过关。
- **用户现实状态高于课程进度**：真实人类不是机器。当你只有 10 分钟、身心疲惫、或被突发的工作线上 Bug 打断时，系统绝不强推大纲，而是动态自适应为微型复习或就地取材教学。
- **零命令交互 (Zero-Command)**：你不需要学习复杂的命令行或配置文件，全程纯自然语言交流，像和真人导师对话一样自然。

---

## 交互范式：你只需要表达意图

系统摒弃了繁重的命令行参数，用户在日常使用中只需表达真实想法：

```text
┌────────────────────────────────────────────────────────┐
│                                                        │
│  “我想系统学习前端开发”                                 │
│  “我想系统搞懂 JavaScript 异步与并发，我只会 async”     │
│  -> 开启新领域的系统学习 (自动诊断并定位最佳切入点)     │
│                                                        │
│  “继续学习”                                            │
│  -> 接续上次断点，自动调取未闭环任务，无废话继续推进    │
│                                                        │
│  “今天加班很累，只有15分钟，简单学一下”                │
│  -> 自动阻断新课，降级为精准复习与轻量演练              │
│                                                        │
│  “我完全不懂闭包，从零教我”                            │
│  “你刚才讲的太抽象了，换一种方式讲讲”                  │
│  “考考我刚才学的，但不要给我任何提示”                  │
│  “先不学教材了，我工作里遇到了一个跨域报错”            │
│  -> 针对性解惑、教学模型突变、闭卷验证或生产实战介入    │
│                                                        │
└────────────────────────────────────────────────────────┘
```

---

## 六层架构体系 (Six-Tier Architecture)

在极简对话界面的背后，运转着一套高严密度的六层工程中枢：

```text
┌─────────────────────────────────────────────────────────────────┐
│ Layer 1: Learner Profile (用户全局画像 / 能力基线 / 盲区归档)    │
├─────────────────────────────────────────────────────────────────┤
│ Layer 2: Knowledge Ingress (三源汇聚与 S0~S5 权威溯源)          │
│   [本地教材库优先 library/]  [Web 官方权威规范]  [真实工程上下文] │
├─────────────────────────────────────────────────────────────────┤
│ Layer 3: Knowledge Map & Topology (领域技能树 / 前置拓扑依赖)   │
├─────────────────────────────────────────────────────────────────┤
│ Layer 4: Adaptive Curriculum Engine (单课动态生长 / 弱项回退)    │
├─────────────────────────────────────────────────────────────────┤
│ Layer 5: Teaching Engine (MCE 极简解释 / 4级策略突变 / 微探针)  │
├─────────────────────────────────────────────────────────────────┤
│ Layer 6: Evidence & Review (分领域闭卷证据链 / 艾宾浩斯抗衰减)   │
└─────────────────────────────────────────────────────────────────┘
```

### 1. 知识来源分级 (S0 to S5)
- **S0 (官方规范)**：ECMAScript Spec, W3C, MDN, Vue/React 官方手册。
- **S1 (经典著作与本地教材)**：本地存入的系统教材 (`library/`)、行业标准权威书籍。
- **S2~S4**：行业进阶课程、一线大厂工程博客、社区排错文章。
- **S5**：AI 参数记忆（必须与 S0/S1 交叉比对，严禁把 AI 自编比喻冒充客观规范事实）。

### 2. 本地教材库优先机制 (Local-First Library)
支持将你自有的电子书、Markdown 笔记、官方教程放入本地 `library/` 目录下（如 `library/frontend/`）。向 AI 提出学习诉求时，系统优先逆向解析本地教材的目录层级作为主干大纲，避免网络散装资料造成的知识混乱。

### 3. 多维度能力核验机制 (Evidence over Scores)
彻底摒弃无意义的“掌握度 85%”等伪精确评分。系统将能力判定解耦为五大客观维度：
- **AI 介入度**：区分无提示独立完成 (`L0`) 与引导下完成 (`L1~L3`)。AI 参与编写的代码一律计为 0% 独立掌握证据。
- **证据维度**：机制阐述 (`E1`)、逻辑心算 (`E2`)、排错诊断 (`E3`)、手写构建 (`E4`)、跨域迁移 (`E5`)。
- **领域专属题型**：概念考辨析与反例、运行时考执行序推演、测试考边界矩阵划分、架构考 7 步权衡链，拒绝所有知识均机械化套用写代码。
- **可逆状态机**：`UNKNOWN -> EXPOSED -> GUIDED -> INDEPENDENT -> TRANSFERABLE -> DURABLE`。一旦后续复杂场景连续失误或延迟抽测失败，状态如实回退至 `REGRESSION DETECTED`。

---

## 快速安装与配置

### 在 Google Antigravity 中运行
本仓库结构原生适配 Antigravity。在当前工作区对话框中直接输入任意自然语言即可开启学习。

### 在 Claude Code 中使用
```bash
# 全局安装 (所有工程通用)
npx skills add https://github.com/1183213030/ai-learning-coach.git --skill ai-learning-coach --global --agent claude-code

# 或单项目安装
npx skills add https://github.com/1183213030/ai-learning-coach.git --skill ai-learning-coach --agent claude-code
```

### 在 OpenAI Codex 中使用
```bash
npx skills add https://github.com/1183213030/ai-learning-coach.git --skill ai-learning-coach --global --agent codex
```

---

## 工程目录结构

```text
ai-learning-coach/
├── SKILL.md                          # 系统核心协议规范 (六层调度法典、仲裁原则)
├── README.md                         # 简体中文主文档
├── README_en.md                      # English Documentation
│
├── knowledge/                        # 动态演化知识注册中心 (概念定义、能力标准、认知陷阱)
│   ├── frontend/                     # 前端与 JavaScript/CSS/浏览器核心
│   └── software-testing/             # 软件测试理论与工程规范
│
├── library/                          # 本地教材库 (Local-First 优先检索物理载体)
│   ├── frontend/                     # 前端工程体系教材
│   └── software-testing/             # 软件测试教材与案例
│
├── references/                       # 核心执行规范与内部调度策略 (Progressive Disclosure)
│   ├── intent-router.md              # 零命令自然语言意图分流与 Teach-vs-Check 隔离规范
│   ├── teaching-protocol.md          # 老师人格、四级策略突变矩阵与微型行为探针
│   ├── curriculum-engine.md          # 现实状态优先调度、拓扑依赖寻路与单课生长
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
