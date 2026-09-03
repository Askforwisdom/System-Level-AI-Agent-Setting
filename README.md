# System-Level-AI-Agent-Setting

在**系统用户层级**上提供一套**统一、规范化的 Agent 设置**：定义 Agent 一般行为规范与环境要求，通过注册登记表集中管理可跨项目调用的 Agent 及其能力，并沉淀可复用的用户级技能（Skills），使所有项目会话遵循同一套约定。

## 使用方式

本仓库内容需放置在**系统用户目录下的 `.agents/` 目录**中才能生效，例如 Windows：

```
C:/Users/<你的用户名>/.agents/
├── AGENTS.md
└── skills/
```

该目录下的 `AGENTS.md` 会在每个会话启动时注入上下文，`skills/` 中的技能供各项目会话按需加载。

## 内容结构

```
├── AGENTS.md                        # Agent 一般行为规范与环境要求 + 系统用户级 Agent 注册登记表
└── skills/                          # 用户级技能定义（SKILL.md）
    ├── agent-init/                  # 会话初始化：加载系统用户级 AGENTS.md 并检查环境
    ├── ai-agent-community/          # 注册登记表查看、注册登记与规范
    ├── behavior-log/                # 项目行为日志记录规范
    └── rhythm/                      # 项目周期性/条件触发行为的节律定义
```

## 说明

- **AGENTS.md**：包含两部分内容：
  - **Agent 一般行为规范与环境要求**：项目工作环境（`AGENTS.md` 与 `.agents` 目录）的构建要求、skills 目录约定、行为日志习惯、规范文本表述要求。
  - **系统用户级 Agent 注册登记表**：登记本机系统用户环境下可跨项目调用的 Agent 及其能力，并定义通过 subagent 使用注册 Agent 的使用约定。新 Agent 的注册只能通过 `ai-agent-community` skill 规范化执行。本仓库版本不包含已注册 Agent 条目（即本机实际登记内容不入库）。
- **skills/**：用户级 skill：
  - `agent-init`：会话初始化时将系统用户目录 `.agents/AGENTS.md` 加载进入上下文（包括子代理会话），并根据其中规范构建、检查当前环境。
  - `ai-agent-community`：系统用户级 Agent 注册登记表的查看、注册登记与规范，是登记表内容的唯一写入入口。
  - `behavior-log`：将所有 Agent 行为记录到项目 `.agents/behavior/log/YYYY-MM.md` 月度日志。
  - `rhythm`：为项目创建/维护 `.agents/rhythm/` 周期性行为节律定义。
