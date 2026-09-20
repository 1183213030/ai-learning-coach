# AI Personal Learning OS (Protocol v1.0)

> A state-machine-driven, evidence-based learning protocol designed for AI Agents (Cursor, Claude Code, Codex, Antigravity) and Web LLMs (ChatGPT, Claude, Gemini).

## 核心理念
- **输出驱动**：用户负责编码、推理、白话表达；AI 负责阻抗调节、挑刺、仲裁与状态持久化。
- **证据链验收**：知识掌握不凭主观感觉，依赖 E1~E5 弹性证据链（Evidence Policy）。
- **解耦架构**：将“学习协议 (Protocol)”、“执行模块 (Modules)”与“记忆状态 (State)”三权分立。

## 跨环境运行模式 (Dual-Mode Execution)

### 模式 A：本地环境 (Local Agent / IDE)
*适用：Cursor, Antigravity, Claude Code, Codex*
- **机制**：Agent 具有直接文件系统读写权限。
- **操作**：
  在对话中输入：`@ai-learning-coach/SKILL.md 读取 state/subjects/typescript.md，继续推进。`
  Agent 会直接修改 `state/` 下的文件，并在每次会话结束时自动写入 `state/sessions/YYYY-MM-DD-{subject}.md`。

### 模式 B：网页环境 (Web AI / No-FS)
*适用：ChatGPT, Claude Web, Gemini Web*
- **机制**：LLM 无法读写本地文件，通过剪贴板作为 IO 桥梁。
- **操作**：
  1. 将 `SKILL.md` 及 `modules/` 放入 Custom GPT / Project Knowledge 中（或首轮附带）。
  2. 粘贴 `state/subjects/{subject}.md` 启动：“以此状态运行协议”。
  3. 会话结束时，AI 会在末尾输出一个 `Session Log` 和更新后的 `Subject State` 代码块，用户复制并存回本地 Git 仓库。
