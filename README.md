# Model & Reasoning Effort Router · 模型与推理强度助手

给刚开始使用 ChatGPT 或 Codex 付费版、想控制用量的用户。按任务推荐模型和推理强度。当前配置能胜任时直接工作，确需换档时才询问，并在答复末尾标明实际配置或注明未核实。

[English](#english) · [场景示例](examples/scenarios.md) · [MIT 许可证](LICENSE)

## 怎么用

- **Codex**：克隆或下载本仓库，将 `plugins/model-effort-router/skills/model-effort-router` 整个目录复制到 `~/.agents/skills/`。在聊天里输入 `$`，选中 `model-effort-router`，然后描述任务。想在本机所有 Codex 聊天中默认使用，可在 `~/.codex/AGENTS.md` 加一条指令，请 Codex 每次按这个 Skill 处理用户消息。 [Skill 安装说明](https://learn.chatgpt.com/docs/build-skills) · [Codex 全局指令](https://learn.chatgpt.com/docs/agent-configuration/agents-md)
- **ChatGPT 网页或手机**：复制[提示词](examples/chat-prompt.md)到聊天里。若希望账号默认采用同样的工作流，把提示词加入 ChatGPT 的自定义指令。 [ChatGPT 自定义指令](https://help.openai.com/en/articles/8096356-chatgpt-custom-instructions)
- **仅看建议**：在任务后加一句「只推荐模型和推理强度」。

## 如何判断与切换

1. 先判断交付目标、所需能力和验收标准。容易返工的模糊需求，先给暂定配置，再复述交付目标，只问一个关键问题。
2. 当前配置能胜任就继续。确需换档时说明原因，通过选择框或文字提供 **是／我自己设置／无所谓**。「是」和「无所谓」都接受推荐。「我自己设置」时给出选择器入口。
3. 客户端提供切换能力时，在授权范围内应用推荐到后续轮次并核实。需要手动切换时，会指明入口。每条答复末尾报告能核实的模型和推理强度。
4. 用量紧张时优先完成关键交付，把更高强度留给容易返工或难以验证的环节。额度以账号用量面板为准。 [模型选择与用量参考](plugins/model-effort-router/skills/model-effort-router/references/models-and-usage.md)

## English

**Model & Reasoning Effort Router** helps people new to paid ChatGPT or Codex choose a model and reasoning effort while managing usage. It clarifies ambiguous requests with one focused question, proceeds when the current configuration fits, and asks before a necessary switch. Where supported and authorized, it can apply settings to a later turn. Otherwise it points you to the model picker. Each reply reports the model and effort when verified.

In Codex, copy [the skill directory](plugins/model-effort-router/skills/model-effort-router) to `~/.agents/skills/` and invoke `$model-effort-router`. In ChatGPT, paste the [workflow prompt](examples/chat-prompt.md) into a chat or your account’s custom instructions. Native skill invocation, clickable choices and model switching depend on the client.

Report reproducible cases in Issues or Discussions when available. Include the client, the task, the suggested configuration and what actually ran.

[MIT License](LICENSE)
