# AGENTS.md - AI Agent 指令体系 v6

!!! 本指令体系采用 AB 双流程架构，请根据当前任务阶段选择对应的子目录指引。

## 架构概览

```
用户需求 → A部分（任务前置准备） → task-spec.md → B部分（任务执行） → 交付成果
```

## 目录结构

| 目录 | 职责 | 入口文件 |
| --- | --- | --- |
| `ai-agent-task-builder/` | A部分：任务前置准备，优化任务描述 | `claude.md` |
| `ai-agent-exec/` | B部分：任务执行，完整实施闭环 | `claude.md` |

## 快速导航

### A部分：任务前置准备
- **入口**：`ai-agent-task-builder/claude.md`
- **核心文件**：
  - `AI-AGENT_preparation.md`：完整流程规范
  - `now-task.md`：用户任务描述输入
  - `undetermined-template.md`：待定项记录模板
- **产出**：`task-spec.md`（任务细则）

### B部分：任务执行
- **入口**：`ai-agent-exec/claude.md`
- **核心文件**：
  - `AI-AGENT_execution.md`：完整执行流程规范
  - `task-spec.md`：任务细则（来自A部分或用户提供）
- **产出**：按任务要求的交付成果

## 使用流程

### 场景一：完整流程（推荐）
1. 用户在 `ai-agent-task-builder/now-task.md` 填写任务需求
2. 进入 A 部分，阅读 `ai-agent-task-builder/claude.md`
3. A 部分产出 `task-spec.md`
4. 进入 B 部分，阅读 `ai-agent-exec/claude.md`
5. B 部分按 `task-spec.md` 执行并交付

### 场景二：跳过A部分
若用户已有清晰明确的任务细则，可直接：
1. 将任务细则保存为 `task-spec.md`
2. 进入 B 部分执行

## AB 部分差异对照

| 维度 | A部分（任务前置准备） | B部分（任务执行） |
| --- | --- | --- |
| 核心目标 | 优化任务描述，产出清晰的任务细则 | 按任务细则执行，完成交付 |
| 运行模式 | 轻量化，无状态记录和git提交 | 完整流程，含状态记录和git提交 |
| 用户交互 | 频繁确认（待定项、优化结果） | 按需交互（阻塞、验证） |
| 产出物 | `task-spec.md` | 按任务要求的交付成果 |
| 返工机制 | 根据用户意见返回分析优化阶段 | 回退到相应环节并记录原因 |

## 通用约定

1. **语言**：所有记录与沟通统一使用简体中文。
2. **MCP调用**：优先使用本地工具；调用MCP前确认权限。
3. **复杂任务**：建议调用 `mcp-sequential-thinking` 进行结构化分析。
4. **时间戳**：所有时间戳必须由 `mcp-time` 服务获取。

## 版本说明

本指令体系为 v6 版本，采用 AB 拆分架构：
- A部分专注任务优化，轻量运行
- B部分专注任务执行，完整闭环
- 两部分通过 `task-spec.md` 衔接
