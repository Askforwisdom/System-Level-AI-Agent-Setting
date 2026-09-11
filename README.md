# System-Level-AI-Agent-Setting

在**系统用户层级**上提供一套**统一、规范化的 Agent 设置**：定义 Agent 一般行为规范与环境要求，通过注册登记表集中管理可跨项目调用的 Agent 及其能力，并沉淀可复用的用户级技能（Skills），使所有项目会话遵循同一套约定。

## 使用方式

将本仓库的 `AGENTS.md` 和 `skills/` 复制到**系统用户目录下的 `.agents/` 目录**，例如 Windows：

```
C:/Users/<你的用户名>/.agents/
├── AGENTS.md
└── skills/
```

按 `agent-init` 技能在会话启动时加载该目录下的 `AGENTS.md`，`skills/` 中的其他技能供各项目会话按需加载。更新已有安装时，保留本机注册登记表中的 Agent 条目。

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
  - **Agent 一般行为规范与环境要求**：项目工作环境（`AGENTS.md` 与 `.agents` 目录）的构建要求、skills 目录约定、行为日志习惯、UTF-8 明文写入建议、规范文本表述要求，以及 Agent 与 subagent 平等和工具能力对等的派发约定。
  - **系统用户级 Agent 注册登记表**：登记本机系统用户环境下可跨项目调用的 Agent 及其能力，并定义通过 subagent 使用注册 Agent 的使用约定。新 Agent 的注册只能通过 `ai-agent-community` skill 规范化执行。本仓库版本不包含已注册 Agent 条目（即本机实际登记内容不入库）。
- **skills/**：用户级 skill：
  - `agent-init`：会话初始化时将系统用户目录 `.agents/AGENTS.md` 加载进入上下文（包括子代理会话），并根据其中规范构建、检查当前环境。
  - `ai-agent-community`：系统用户级 Agent 注册登记表的查看、注册登记与规范，是登记表内容的唯一写入入口。
  - `behavior-log`：将所有 Agent 行为记录到项目 `.agents/behavior/log/YYYY-MM.md` 月度日志，使用 Write 工具的 `mode=append` 在文件末尾追加，保留历史记录并记录错误与使用不便。
  - `rhythm`：为项目创建/维护 `.agents/rhythm/` 周期性行为节律定义。

## 同步维护

以系统用户目录中的 `.agents/AGENTS.md` 和 `.agents/skills/` 为来源，覆盖更新仓库根目录的 `AGENTS.md` 与 `skills/`。同步后的 `AGENTS.md` 清空“注册 Agent”小节中的具体登记条目，保留登记表说明、注册提示和使用约定，并同步更新本 README。

项目 `.agents/` 用于保存本地行为日志等运行状态，已通过 `.gitignore` 排除，不推送到远程仓库。
