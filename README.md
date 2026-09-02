# System-Level-AI-Agent-Setting

系统用户级 AI Agent 设置仓库：维护可跨项目复用的 Agent 注册登记表与技能（Skills）定义。

## 内容结构

```
├── AGENTS.md                        # 系统用户级 Agent 注册登记表 + 使用约定
└── skills/                          # 用户级技能定义（SKILL.md）
    ├── behavior-log/                # 项目行为日志记录规范
    ├── register-project/            # 新 Agent 注册到登记表的规范流程
    └── rhythm/                      # 项目周期性/条件触发行为的节律定义
```

## 说明

- **AGENTS.md**：登记本机系统用户环境下可跨项目调用的 Agent 及其能力，每个会话启动时注入上下文；同时定义了通过 subagent 使用注册 Agent 的使用约定与行为日志要求。
- **skills/**：用户级 skill，供各项目会话按需加载：
  - `behavior-log`：将所有 Agent 行为记录到项目 `.agents/behavior/log/YYYY-MM.md` 月度日志。
  - `register-project`：将新 Agent 规范化注册到系统用户级 Agent 注册登记表的唯一入口。
  - `rhythm`：为项目创建/维护 `.agents/rhythm/` 周期性行为节律定义。

## 同步范围

`.agents/` 目录（行为日志、节律等本机运行状态）为本机私有，不同步至远端，已在 `.gitignore` 中排除。
