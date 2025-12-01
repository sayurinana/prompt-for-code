# AGENTS.md - A部分：任务前置准备

!!! 在开始任何工作前，必须先阅读本文件，并查阅`ai-agent-task-builder/`目录中的所有指引。

## 快速指引

- `ai-agent-task-builder/AI-AGENT_preparation.md`：任务前置准备的完整流程规范。
- `ai-agent-task-builder/undetermined-template.md`：待定项记录的格式模板。
- `ai-agent-task-builder/now-task.md`：待用户填写的任务描述文件。

## 职责定位

A部分专注于**任务前置准备**，引导用户优化任务描述，产出清晰明确、可落地的最终任务细则。

## 核心流程

```
now-task.md → 分析优化 → undetermined.md → 用户确认 → optimized-task.md → 用户确认
                ↑                                                              ↓
                └────────────── 不满意：根据用户意见返工 ←─────────────────────┘
                                                                               ↓
                                                      满意 → 重命名为task-spec.md → A结束
```

## 工作要点

1. **轻量化运行**：A过程不使用csv状态记录和git提交操作，专注于任务优化。
2. **待定项处理**：所有优化方案必须经用户确认后方可纳入最终任务细则。
3. **返工机制**：若用户不满意，根据具体意见返工到分析优化环节。
4. **最终产出**：`task-spec.md`，作为B部分的输入依赖。

## 产出物说明

A过程结束后，将`optimized-task.md`重命名为`task-spec.md`，交付给B部分使用。
