---
name: agent-init
description: 在项目 Agent 的会话初始化时，确认当前项目 Agent 的 AGENTS.md 已进入上下文，并加载系统用户级 Agent 的 AGENTS.md；依据两者规范检查当前项目 Agent 的核心构成并载入相关 skill。
---

# 会话初始化：加载项目 Agent 定义

会话初始化时：

1. 确认当前项目 Agent 根目录中的 `AGENTS.md` 已进入上下文。
2. 加载系统用户级 Agent 的 `AGENTS.md`（如 `C:/Users/<用户名>/.agents/AGENTS.md`）。
3. 根据两者规范检查当前项目 Agent 的核心构成。
4. 识别并载入与当前任务相关的项目级和系统用户级 skill。

Agent 与 subagent 均采用上述初始化方式。
