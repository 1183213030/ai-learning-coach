# Frontend Knowledge System v1 落地实施计划与仓库审计报告

> **目标**：在不推翻现有协议、不删除学员历史记录、不进行破坏性重构的前提下，严格遵循 `ai-learning-coach` Protocol V3.2.0/V3.2.1 架构，平滑接入「前端权威教材知识库 (Frontend Knowledge System v1)」。
> **审计日期**：2026-11-17
> **执行原则**：最小改动原则 (Minimal Touch)、分层架构原则（权威索引注册表 + 本地核心摘要 + 零代码库膨胀）、现有学员档案绝对保护原则。

---

## 一、 仓库全面结构审计结论 (Audit Findings)

### 1. `README.md` 与 `SKILL.md` 审计
- **当前协议版本**：`Protocol V3.2.0`（配套引用规范遵循 `Protocol V3.2.1`）。
- **最高行动指南 (Prime Directive)**：三维完整性（知识完整 Knowledge Completeness、教学完整 Teaching Completeness、能力完整 Capability Completeness）。
- **三维独立状态机**：
  1. 知识覆盖状态：`unknown -> partial -> covered`
  2. 教学实施状态：`pending -> in_progress -> delivered`
  3. 学员能力状态：`not_attempted -> attempted -> supported -> independent -> transfer_verified`
- **能力考核阶梯**：
  - 双层能力分级：**概念独立掌握**（Concept Mastery，要求所有必选维度在无提示闭卷 `L0` 下 $\ge \text{independent}$）与 **工程实战精通**（Engineering Mastery，要求在实际业务代码中达成 `transfer_verified`）。
  - 提示梯阶：`L0`（0% AI 提示，完全独立闭卷）至 `L5`（100% AI 代写）。仅 `L0` 计入独立能力。
  - 证据链等级：`E1` 概念解释、`E2` 输出预测、`E3` 独立构建、`E4` 边界排错、`E5` 极端变异。
  - 可逆降级机制：后续复杂任务中一旦暴露盲区，立即触发 `REGRESSION DETECTED` 状态回退。
- **资料检索与摄入规则 (Ingress Priority Cascade)**：
  - 第一优先级：`library/<domain>/` 本地教材/笔记（S1/S2），作为主干课程骨架。
  - 第二优先级：Web Research 权威规范（S0/S1），作为事实校准依据。
  - 第三优先级：Project Context 项目代码与 Git Diff，作为实战检验土壤。
- **结论**：现有顶层协议逻辑严密、自洽，完全支持外部权威教材的索引化接入，无需任何协议层改动。

---

### 2. `knowledge/frontend/` 知识点定义格式审计
- **现有结构**：
  - 维度定义：`knowledge/dimensions/javascript.yaml`、`knowledge/dimensions/universal.yaml` 已完善定义语义维度。
  - 现有知识点：`closure.yaml`、`equality.yaml`、`event-loop.yaml`、`includes.yaml`、`scope.yaml`。
  - 待填充空目录：`knowledge/frontend/browser/`、`knowledge/frontend/security/`。
- **规范标准 (以 `includes.yaml` 为 Golden Spec)**：
  - 规范版本：`version: "3.2.1"`
  - 核心元数据：`concept.id`, `concept.name`, `concept.domain`, `concept.source_ids`, `concept.normative_sources`（明确区分 S0/S1 级别与章节引用）。
  - 权威声明表：`claims`（必须标记 `semantic_layer: "ecmascript" | "html" | "browser" | "engine" | "framework"`，杜绝跨层污染）。
  - 行为边界矩阵：`boundary_matrix`（每一项包含 `dimension`, `applicability: "required" | "optional" | "not_applicable"`, `reason`, `coverage`；标记 `not_applicable` 时必须提供带 S0 章节号的 `rationale` 证明）。
  - 覆盖工件与受控变异：`coverage_artifacts`（包含 `artifact_id`, `dimension`, `claim_id`, `discriminates`, `discriminative_power`, `case.baseline`, `case.mutation`，必须证明单一语义维度变异）。
- **结论**：知识点契约已具备极其成熟的工业级 Schema，新接入的前端概念必须严格按照此 Schema 编写。

---

### 3. `library/frontend/` 本地教材存放结构审计
- **现状**：
  - `library/frontend/` 目录存在，但**当前为空 (0 文件)**。
  - 仓库内存在历史遗留的 `library/Web` 目录（存放了一整套抓取的前端面试笔记教程 `00-前端工具` ~ `17-资源推荐`）。
- **对齐分析**：
  - 严禁把 MDN、JavaScript.info 或 The Odin Project 的数十兆网页全量克隆或下载至 `library/frontend/`（这会导致上下文瞬间爆炸、搜索命中大量过期/垃圾信息）。
  - 应采取**“索引注册表 + 本地轻量大纲与错题”**模式：`library/frontend/` 仅存放课程索引纲要（Syllabus Index）与练习任务清单，正文通过 URL 精确映射按需查阅。

---

### 4. `references/` 知识来源与教学约束规则审计
- **现状**：包含 15 个核心规范文档：
  - `claim-evidence-protocol.md`（S0/S1 溯源与语义层隔离规范）
  - `dimension-applicability-protocol.md`（维度适用性审计与完备性计算公式）
  - `concept-boundary-engine.md`（单变量受控变异与案例质量门禁）
  - `coverage-state-machine.md`（知识/教学/能力三维状态机流转细则）
  - `teaching-protocol.md`（私教人设与初学者单回合 2 维度认知预算）
  - `curriculum-engine.md`（动态前置依赖树与现实 Bug 优先法则）
  - `knowledge-discovery.md`（三大知识摄入支柱与 S0~S5 权威分级表）
  - `local-library.md`（本地教材优先摄入协议）
  - `evidence-model.md`（独立能力闭卷 L0 评定标准）
  - `review-system.md`（艾宾浩斯复习调度算法）
  - `socratic-hints.md`（L0~L5 阶梯式提示法）
- **结论**：所有教学动作已有严谨的法典约束，接入新教材时无缝继承现有规则。

---

### 5. `templates/`（特别是 `source-manifest.yaml`）字段结构审计
- **现状**：`templates/source-manifest.yaml` 为系统正式的资料登记册，字段规范如下：
  ```yaml
  version: "2.1.0"
  last_updated: "2026-09-30T09:20:00Z"

  sources:
    - id: "src-mdn-web"
      title: "MDN Web Docs"
      type: "official_documentation"
      tier: "S0"
      url: "https://developer.mozilla.org"
      role: "Standard reference for JavaScript runtime, DOM, and Web APIs"
    - id: "src-local-testing-book"
      title: "Software Testing Foundations (Local Textbook)"
      type: "local_textbook"
      tier: "S1"
      path: "library/software-testing/testing-fundamentals.md"
      role: "Primary curriculum backbone for software testing methodology and case design"

  coverage_mapping:
    "knowledge/frontend/javascript/scope.yaml":
      source_ids: ["src-mdn-web"]
  ```
- **结论**：格式极其清晰、扩展友好，只需在 `sources` 下增量注册新权威教材，并在 `coverage_mapping` 中绑定对应知识点文件。

---

### 6. `evals/` 教学质量评测用例审计
- **现状**：包含 8 套自动化与准则评测：
  - `anti-answer-dumping.md`（防答案倒灌）
  - `anti-fake-mastery.md`（防“懂了”假掌握，必须闭卷验证）
  - `applicability-eval.md`（维度适用性审计合规性）
  - `boundary-coverage-eval.md`（边界矩阵与工件辨别力校验）
  - `claim-source-eval.md`（防规范跨层混淆，如禁止把 V8 GC 当作 ECMAScript 语法规约）
  - `coding-learning-evals.md`（防 AI 代码代写，强化 Git Diff 实际项目提炼）
  - `controlled-variation-eval.md`（单语义维度受控变异校验）
  - `teaching-completeness-eval.md`（渐进教学 vs 边界完整性平衡校验）
- **结论**：评测集健全，新教材引入后的所有教学输出将自动受到上述门禁的严格保护。

---

### 7. 关键现状发现：学员当前学习进度
- 检查 `state/subjects/frontend.md` 发现：
  - 学员已经 100% 通关了 **Level 1 (Syntax & API Semantics)** 与 **Level 2 (Runtime Derivation & Protocols)**。
  - **当前活跃攻关节点**：`Level 3: 核心机制与手写实战` 中的 **`FE-L3-A1: 手写 Promise A+ 规范 (链式调用与值穿透)`**（处于 `RUNNING` 与 `EXAM` 考核阶段）。
  - **错题档案**：明确记录了学员在 Promise 三种状态机流转与不可逆守卫上的混淆点。
  - **知识库缺口**：`knowledge/frontend/javascript/` 目录下目前**缺少 `promise.yaml`**。
  - **落地策略机遇**：将 JavaScript.info (S1) 和 MDN (S0) 作为事实依据，首发落地 `promise.yaml`，可以直接赋能学员当前的攻坚点！

---

## 二、 最小改动文件清单 (File Modification Plan)

遵循“不删减已有历史、最小变动、增量扩展”原则：

| 操作类型 | 文件相对路径 | 变更说明 |
| :--- | :--- | :--- |
| **MODIFIED** | `templates/source-manifest.yaml` | 增量注册 4 个核心权威来源（MDN Curriculum, JavaScript.info, The Odin Project, Vue/TS 官方文档），保留原有测试与基础来源，更新映射关系。 |
| **CREATED** | `library/frontend/README.md` | 本地前端资料库目录指引与轻量索引说明（遵循 Local-First 协议）。 |
| **CREATED** | `library/frontend/mdn-curriculum-index.md` | MDN 核心大纲索引（S0 主线：HTML/CSS/JS 进阶路径与规范章节映射）。 |
| **CREATED** | `library/frontend/javascript-info-index.md` | JavaScript.info 核心原理索引（S1 专项：闭包、原型、事件循环、Promise、V8 机制映射）。 |
| **CREATED** | `library/frontend/odin-project-tasks.md` | The Odin Project 实战验收题库索引（S2 实践：计算器、待办列表、实战项目标准）。 |
| **CREATED** | `knowledge/frontend/javascript/promise.yaml` | 为学员当前攻坚的 `FE-L3-A1` 补充标准的 Concept Boundary Contract V3.2.1 契约文件。 |
| **PRESERVED** | `state/subjects/frontend.md` | **保持 100% 完整**，不清除任何学员已通关节点、复习队列和错题记录。 |
| **PRESERVED** | `SKILL.md` 及 `references/*.md` | **保持 100% 完整**，全量继承原有调度与防泄题规则。 |

---

## 三、 首批权威教材注册方案 (`templates/source-manifest.yaml`)

将要在 `templates/source-manifest.yaml` 增量注入的具体配置段落如下：

```yaml
  # === Frontend Knowledge System v1 权威教材注册 ===
  - id: "src-mdn-curriculum"
    title: "MDN Web Development Curriculum & Standards"
    type: "official_curriculum"
    tier: "S0"
    url: "https://developer.mozilla.org/en-US/docs/Learn_web_development"
    role: "主线大纲：标准 Web 平台能力全景、HTML/CSS/JS 学习路径与标准规范对齐"
    coverage_domains: ["frontend-core", "dom-apis", "web-standards"]

  - id: "src-javascript-info"
    title: "The Modern JavaScript Tutorial (JavaScript.info)"
    type: "authoritative_book"
    tier: "S1"
    url: "https://javascript.info"
    role: "深度专项：ECMAScript 底层运行机制、执行上下文、闭包、原型链、事件循环与 Promise A+ 原理"
    coverage_domains: ["javascript-internals", "async-runtime", "v8-mechanisms"]

  - id: "src-odin-project"
    title: "The Odin Project (Full Stack Curriculum)"
    type: "vetted_course"
    tier: "S2"
    url: "https://www.theodinproject.com/paths/foundations/courses/foundations"
    role: "实战题库：闭卷动手编码任务库、阶段性综合项目验收标准与工程踩坑防线"
    coverage_domains: ["practical-projects", "engineering-drills"]

  - id: "src-vue-official"
    title: "Vue.js Official Documentation & RFCs"
    type: "official_documentation"
    tier: "S0"
    url: "https://vuejs.org"
    role: "现代前端框架标准：响应式底层原理 (Proxy/Reflect) 与组件生命周期权威依据"
    coverage_domains: ["vue-architecture"]

  - id: "src-typescript-official"
    title: "TypeScript Official Handbook"
    type: "official_documentation"
    tier: "S0"
    url: "https://www.typescriptlang.org/docs"
    role: "类型系统权威依据：类型推导、条件类型、类型体操与工程契约"
    coverage_domains: ["typescript-core"]
```

---

## 四、 落地执行四阶段计划 (Rollout Roadmap)

```text
阶段一：来源注册 (Phase 1)
  └─ 在 templates/source-manifest.yaml 中注册 5 个权威来源，保留旧来源与现有映射。

阶段二：大纲与索引构建 (Phase 2)
  └─ 在 library/frontend/ 创建轻量级章节索引与题库映射文档（保持轻量，非大篇幅下载）。

阶段三：当前攻坚原子契约落地 (Phase 3)
  └─ 为学员当前处于 RUNNING 状态的 FE-L3-A1 创建 knowledge/frontend/javascript/promise.yaml，
     基于 JavaScript.info (S1) 和 ECMAScript/Promise A+ (S0) 构建完整的概念边界矩阵。

阶段四：无缝恢复教学 (Phase 4)
  └─ 学员输入标准唤醒指令，系统自动识别 Level 3 进度与新注入的权威资料库，开启沉浸式带练。
```
