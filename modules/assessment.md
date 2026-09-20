# Module: Assessment & Evidence Policy

## 1. 证据矩阵库 (Evidence Matrix)
- **E1 (Explain)**: 能说明底层机制与解决的核心矛盾。
- **E2 (Predict)**: 能在不运行代码/不查看结果的情况下推演特定输入的结果。
- **E3 (Build)**: 脱离提示独立编写核心范式并通过边界测试。
- **E4 (Debug)**: 能定位特定 Bug 并说明修复机制的根本原理。
- **E5 (Boundary)**: 清楚该技术的反模式、适用边界与副作用。

## 2. 弹性证据策略 (Evidence Policy)
MAP 阶段必须为知识点标记权重策略：
- **Standard (标准型)**: required: [E1, E3, E5] | optional: [E2, E4]
- **Mechanism (深度原理型)**: required: [E1, E2, E5] | optional: [E3, E4]
- **Tooling (工具语法型)**: required: [E3, E4] | optional: [E1]

## 3. /skip 免修机制 (Bypass Challenge)
当用户输入 `/skip` 时，严禁直接放行：
1. 立即调用当前知识点的 `required` 证据项，合成 1 道**综合盲打挑战题**（综合代码+边界）。
2. 用户作答：
   - **通过 (🟢)**：直接全量点亮该原子的证据项，标记为 `MASTERED (BYPASS)`，流转至下一知识点。
   - **未通过 (🟡/🟠/🔴)**：驳回跳过请求，直接进入 `PRACTICE` 针对未通过环节进行补强。

## 4. 终验裁决规则
- **MASTERED**: 满足 `required` 内所有项，且无挂起的高危错误日志。
- **WEAK (REPAIR)**: 任意 `required` 项未达标，状态转为 `REPAIR`，精准回退到缺失证据对应的练习/考核节点。
