# AI Agent 指令体系 v6

面向 AI Agent 的任务执行指令框架，采用 AB 双流程架构实现任务优化与执行的解耦。

## 特性

- **AB 拆分架构**：A 部分专注任务优化，B 部分专注任务执行
- **轻重分离**：A 部分轻量运行，B 部分完整闭环
- **标准化衔接**：通过 `task-spec.md` 连接两部分
- **灵活入口**：支持完整流程或跳过 A 部分直接执行

## 目录结构

```
ai-agent-memo-6/
├── claude.md                      # 顶层入口指引
├── README.md                      # 本文件
├── ai-agent-task-builder/         # A部分：任务前置准备
│   ├── claude.md                  # A部分入口
│   ├── AI-AGENT_preparation.md    # 前置准备流程规范
│   ├── now-task.md                # 用户任务描述输入
│   └── undetermined-template.md   # 待定项记录模板
└── ai-agent-exec/                 # B部分：任务执行
    ├── claude.md                  # B部分入口
    └── AI-AGENT_execution.md      # 执行流程规范
```

## 快速开始

### 完整流程（推荐）

1. 在 `ai-agent-task-builder/now-task.md` 填写任务需求
2. AI Agent 阅读 `ai-agent-task-builder/claude.md` 进入 A 部分
3. A 部分完成后产出 `task-spec.md`
4. AI Agent 阅读 `ai-agent-exec/claude.md` 进入 B 部分
5. B 部分按任务细则执行并交付

### 跳过 A 部分

若已有清晰的任务细则：
1. 将任务细则保存为 `task-spec.md`
2. AI Agent 直接进入 B 部分执行

## 流程概览

### A部分：任务前置准备

```
now-task.md → 分析优化 → undetermined.md → 用户确认 → optimized-task.md → 用户确认 → task-spec.md
```

- **目标**：优化任务描述，产出清晰可执行的任务细则
- **特点**：轻量运行，无状态记录和 git 提交
- **产出**：`task-spec.md`

### B部分：任务执行

```
task-spec.md → 流程设计 → 任务主体流程循环 → 验证结果 → 文档更新 → 收尾
```

- **目标**：按任务细则执行，完成交付
- **特点**：完整闭环，含状态记录和 git 提交
- **产出**：按任务要求的交付成果

## 核心文件说明

| 文件 | 用途 |
| --- | --- |
| `now-task.md` | 用户填写原始任务需求 |
| `undetermined.md` | A 部分产出的待定项列表（需用户确认） |
| `optimized-task.md` | A 部分优化后的任务描述 |
| `task-spec.md` | 最终任务细则，AB 部分的衔接文件 |
| `AI-AGENT_working-status.csv` | B 部分的状态记录文件 |

## 适用场景

- 需要 AI Agent 执行复杂软件工程任务
- 任务描述需要优化和明确
- 需要完整的执行过程追踪
- 多轮迭代的任务开发

## 版本历史

- **v6**：AB 拆分架构，任务优化与执行解耦
