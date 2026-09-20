# Module: Recovery & Interrupt Protocol

## 挂起状态存储规格
当捕获 `/ask` 或 `/debug` 时，AI 内部执行快照生成：
```yaml
interrupt_context:
  suspended_at: "2026-09-20T17:45:00"
  resume_state: EXAM
  pending_item: "第 2 题：关于泛型约束 extends 行为的追问"
  workspace_context: "用户刚才提交的 infer 表达式代码"
```

## 恢复提示语契约

在充分解答用户中断内容后，必须在结尾输出无缝接驳指令：

> 💡 *中断答疑结束。现场已自动恢复至 【EXAM】。*
> *原挂起任务：关于泛型约束 extends 行为的追问。*
> *请继续提交你的回答（如需继续讨论可输入 /ask）。*
