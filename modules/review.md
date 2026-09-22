# Module: Ebbinghaus Spaced Review Engine

## 1. 艾宾浩斯复习阶梯 (Interval Tiers)
已通关的原子知识点纳入 6 级遗忘曲线复习阶梯：

| 阶梯 (Stage) | 间隔时间 (Interval) | 目标状态 |
| :--- | :--- | :--- |
| **Stage 1** | +1 天 (24 小时) | 次日即时强化 |
| **Stage 2** | +2 天 (48 小时) | 短期抗衰减 |
| **Stage 3** | +4 天 (96 小时) | 结构内化复核 |
| **Stage 4** | +7 天 (1 周) | 中期心智稳固 |
| **Stage 5** | +15 天 (半个月) | 跨模块迁移抗阻 |
| **Stage 6** | +30 天 (1 个月) | 长期巩固 (PERMANENT) |

---

## 2. 到期状态判定 (Review Status Algorithm)
每次加载学科状态时，比对当前日期 (`today`) 与知识点的 `next_review_due`：
- **HEALTHY**：`today < next_review_due`（未到期，无需处理）
- **DUE**：`today == next_review_due`（恰好到期，触发门禁抽测）
- **OVERDUE**：`today > next_review_due`（逾期未复习，高衰退风险，优先强制抽测）

---

## 3. 抽测出题规范 (Spot Exam Generation)
复习抽测不重复全套流程，而是从该知识点绑定的核心证据项中，精准提取 1 道**极简高浓度题目**：
1. **优先提取 E2 (Predict)**：给出一小段包含上下文边界的代码，要求心算推演输出或执行时序。
2. **或提取 E3 (Build)**：脱离提示，在 5~10 行内白板手写核心范式关键实现。
3. **或提取 E4 (Debug)**：诊断一段包含经典易混淆陷阱的代码片段。

> **出题原则**：单轮出题，单次仅测 1 个知识点，不带引导性提示。

---

## 4. 考核判定与阶梯迁移 (Rating & Decay Transitions)

| 抽测评级 | 阶梯变化 | 状态机动作 | 下次复习日期计算 |
| :--- | :--- | :--- | :--- |
| **Mastered (PASS)** | `Stage = min(Stage + 1, 6)` | 巩固成功，返回原主线 | `next_review_due = today + interval(Stage)` |
| **Basically Sound (SOUND)** | `Stage` 保持不变 | 指出认知细节盲区，继续主线 | `next_review_due = today + interval(Stage)` |
| **Logic Flaw (FLAW)** | `Stage = max(1, Stage - 1)` | 标记为轻度退化，追加 1 道靶向题 | `next_review_due = today + 1` |
| **Not Mastered (FAIL)** | 重置为 `Stage 1` | **严重衰退**：从 `mastered_atoms` 剔除，移入 `weak_atoms`，强制打回 `REPAIR` 环路 | 重新通过终验后重置计时 |

---

## 5. 门禁流转规则 (Review Gate Protocol)
1. **自动门禁 (`REVIEW_GATE`)**：
   - 每次会话启动进入 `INIT` 后，系统自动扫描 `status == DUE` 或 `OVERDUE` 的知识点。
   - 若存在待复习项：单次会话最多优先执行 **1~2 个知识点** 的抽测，避免占用过多主线精力。
   - 抽测完成（或无待复习项）后，平滑流转至 `CORE_20` 开启本次新知识点。
2. **主动触发 (`/review`)**：
   - 用户任何时刻输入 `/review`，系统列出当前学科的复习清单（含各 Stage 分布与逾期项），并立即唤醒首个待复习知识点的考核。
