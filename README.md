# System-Level-AI-Agent-Setting

系统用户级 Agent 的通用规范与技能模板。`AGENTS.md` 定义项目 Agent 的构成、运行约定及系统用户级 Agent 注册登记表格式；`skills/` 提供会话初始化、Agent 注册、行为日志和行为节律的可复用技能。

## 安装与更新

将仓库根目录的 `AGENTS.md` 和 `skills/` 放入系统用户级 Agent 根目录。Windows 示例：

```text
C:/Users/<用户名>/.agents/
├── AGENTS.md
└── skills/
```

首次安装后，可按本机需要在 `AGENTS.md` 的“注册 Agent”小节登记 Agent。更新已有安装时，先保留本机的注册条目和适配内容，再同步仓库中的通用规范与技能；仓库版 `AGENTS.md` 不含这些本机内容。

项目会话按 `agent-init` 加载项目和系统用户级 Agent 的 `AGENTS.md`，并按任务载入相关技能。

## 仓库内容

| 路径 | 用途 |
|---|---|
| `AGENTS.md` | 项目 Agent 核心构成与运行规范；系统用户级 Agent 注册登记表模板和使用约定。 |
| `skills/agent-init/` | 会话初始化时加载项目与系统用户级定义，并检查核心构成、载入相关技能。 |
| `skills/ai-agent-community/` | 查看和维护系统用户级 Agent 注册登记表。 |
| `skills/behavior-log/` | 将项目 Agent 行为记录到目标项目 `.agents/behavior/log/YYYY-MM.md`。 |
| `skills/rhythm/` | 定义项目 Agent 的周期性或条件触发行为。 |

## 同步来源

本仓库的 `AGENTS.md` 与 `skills/` 以系统用户级 Agent 根目录中的同名内容为来源。同步 `AGENTS.md` 时，移除“本机适配”小节和“注册 Agent”小节中的具体条目，保留登记表说明、注册提示及使用约定；`skills/` 则按来源覆盖更新。

仓库的 `.agents/` 保存本项目运行时的行为日志等内容，由 `.gitignore` 排除，不推送至远程仓库。
