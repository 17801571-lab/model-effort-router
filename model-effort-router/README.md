# Model & Effort Router

一个面向刚开始使用 ChatGPT 或 Codex 付费版的用户的 Skill。直接说你想做什么。任务还模糊时，它会问一个能帮你想清目标的问题；任务清楚后，它会判断需要什么模型和推理强度。遇到 5 小时或周用量紧张时，先做必须交付的部分，并给关键步骤留出验证空间。

| 用法 | 示例 | Skill 的下一步 |
| --- | --- | --- |
| 仅推荐 | 「这份报告要核对三份来源。帮我选模型和强度，只推荐。」 | 给一个首选，必要时给一个备选 |
| 先确认 | 「帮我定位测试间歇失败。先建议配置，我确认后再做。」 | 推荐并等你回复「好」或「沿用」 |
| 默认自动匹配 | 「把这份清单转成表格。」 | 当前设置能达标时直接完成，末尾标明配置 |
| 引导澄清 | 「我想为《清明上河图》做个课堂视频。」 | 先给暂定模型与强度，再复述课堂用途，最后问「你希望学生看完后能在画里指出什么？」；你也可以说「你定」 |
| 分阶段执行 | 「先定位结算故障。第二阶段需要换模型或加强推理时再问我。」 | 完成已授权阶段，在确需调整的交接点暂停 |

在支持自动切换的界面，首次需要确定切换方式时会问「我会按任务自动选模型和强度。需要我自动切换吗？」可选「自动切换」或「手动切换」。同一对话只问一次，明显增加用量或超出已授权阶段的调整再确认。

「好」表示接受推荐，「沿用」表示保留当前配置。主会话的下一轮设置由产品选择器或接入了相关能力的宿主控制。需要手动操作时，可以切完直接回「已切换」。账户剩余量以用量面板为准。 [模型选择器](https://learn.chatgpt.com/docs/models) · [Codex App Server](https://learn.chatgpt.com/docs/app-server) · [用量与价格](https://learn.chatgpt.com/docs/pricing)

确实需要你决定时，Skill 会在可用的客户端显示「好」「沿用」选择框，或接受同样的文字回复。模型选择和权限审批各自处理。Skill 生效期间，每条答复末尾一行回顾实际模型和强度。无法核实的设置会标为未知，建议会注明「推荐」。 [选择输入与权限审批](https://learn.chatgpt.com/docs/app-server)

## 在 Codex 中试用

从仓库根目录运行以下命令，把 [Skill 目录](plugins/model-effort-router/skills/model-effort-router) 安装到个人技能目录。也可将同一文件夹放到目标项目的 `.agents/skills/`。如果同名 Skill 已存在，先查看内容，再决定是否替换。

```sh
mkdir -p "$HOME/.agents/skills"
cp -Rn plugins/model-effort-router/skills/model-effort-router "$HOME/.agents/skills/"
```

在输入框中选择 `$model-effort-router`，例如输入 `$model-effort-router 先推荐配置。我需要核对三份合同的日期字段，然后输出差异表。` CLI 也可用 `/skills` 找到它。如果选择器没有更新，重启 Codex。使用 Skill 工作时，CLI 用 `/model` 查看模型和强度，可用 `/status` 查看当前模型及可用的用量信息。 [安装与调用 Skill](https://learn.chatgpt.com/docs/build-skills) · [Codex 用量入口](https://learn.chatgpt.com/docs/pricing)

## 在 ChatGPT 中试用

- **普通聊天，最快上手**。把 [聊天提示词](examples/chat-prompt.md) 粘贴到新对话，接着描述任务。普通 Chat 按本账户选择器显示的 Instant、Medium、High 等选项给建议。 [ChatGPT 模型和套餐](https://help.openai.com/en/articles/20001354-gpt-6-and-other-models-in-chatgpt)
- **支持本地插件的 ChatGPT 桌面版**。仓库带有可移植插件及本地 Marketplace 清单。用 `codex plugin marketplace add .` 注册当前仓库。在支持的桌面 Work 或 Codex 客户端，从 Plugins 中选择该源并安装 `model-effort-router`。在支持 `plugin add` 的 Codex CLI 中，可执行 `codex plugin add model-effort-router@model-effort-router-marketplace`，再用 `/skills` 选择插件内的 `model-effort-router:model-effort-router`。网页、移动端或受管理的工作区，请以该界面实际提供的插件分发入口为准，也可以使用上面的聊天提示词。 [插件打包与分发](https://developers.openai.com/plugins/build/plugins) · [Codex 插件命令](https://learn.chatgpt.com/docs/developer-commands?surface=cli)

如果希望它处理当前对话中的后续请求，可以说「这段对话都用 Model & Effort Router」。跨项目安装使用个人技能目录。是否隐式调用由产品和任务匹配决定。

## 提交反馈

欢迎通过 Issues 或 Discussions（若已启用）分享任务样例。附上使用界面、可选模型和强度、可公开的任务摘要、推荐设置、实际使用的设置，以及结果是否达到验收标准。如果比较用量，记录面板中两次运行各自显示的区间，并注明期间是否有其他任务。模型和用量规则有变化时，欢迎提交官方链接与核对日期。 [模型和用量参考](plugins/model-effort-router/skills/model-effort-router/references/models-and-usage.md) · [试用用例](examples/scenarios.md)

## English quick start

An instruction-only skill for people new to a paid ChatGPT or Codex plan. Clear tasks proceed directly. When a request is underspecified, the skill asks one focused question or proceeds with a reasonable assumption if you delegate. Each reply ends with one line showing the verified model and reasoning effort, or a clearly labeled recommendation. Copy the skill folder to `~/.agents/skills/` for Codex, or paste the [chat prompt](examples/chat-prompt.md) into ChatGPT. Actual model changes depend on your client.

Licensed under [MIT](LICENSE).
