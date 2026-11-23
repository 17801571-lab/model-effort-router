# 产品、模型和用量

核对日期为 2026-11-23。以下是推荐起点。实际可用组合取决于账户、客户端、工作区和发布进度。优先采用当前选择器或宿主返回的选项。只在用户问最新型号、标签有冲突或需要确定可用性时查对应的官方页面。

## ChatGPT 普通聊天

| 任务 | Plus 用户可优先考虑 |
| --- | --- |
| 短改写、明确格式转换、简短问答 | Instant（界面可见时） |
| 多约束写作、比较方案、需要推导和检查的问题 | Medium |
| 开放式分析、证据冲突、需要更严谨的推导 | High |

官方当前将 Medium 和 High 列入 Plus，Extra High 与 Pro 的资格取决于套餐。GPT-6.2 Astra 与 Sol 的上述型号选择面向 Work 与 Codex；普通 Chat 按自己的菜单选择。普通 Chat 的选项标签与 Work/Codex 推理档位各自定义。若界面提供自动路由，它由产品控制。 [ChatGPT 模型与套餐](https://help.openai.com/en/articles/20001354-gpt-6-and-other-models-in-chatgpt) · [GPT-6.2 发布说明](https://learn.chatgpt.com/docs/whats-new/gpt-62-astra-sol)

## ChatGPT Work 和 Codex

| 可用模型 | 建议用于 | 强度起点 |
| --- | --- | --- |
| GPT-6 Luna | 小范围编辑、字段提取、格式转换、输入和验收明确的高频任务 | Light（CLI 为 Low）或当前较低档 |
| GPT-6.1 Terra | 截图分析、视觉检查、浏览器或桌面操作 | Light 或 Medium，按交互和验收难度选 |
| GPT-6.2 Sol | 日常代码修改、常规多步交付、文稿起草、测试与复核 | Light；多步骤协调或风险较高时用 Medium |
| GPT-6.2 Astra | 跨模块疑难故障、复杂证据整合、多约束工程决策 | Medium 起步；遇到具体且难验证的推理瓶颈时考虑 High 或 Extra High |

这些搭配是本项目依据官方模型定位给出的建议。型号缺失时，在当前菜单里找能完成相同工作的可用模型。对于有清晰验收标准的任务，优先降低推理强度再观察结果；对于需要高判断力的任务，选择足够的模型能力后再微调强度。 [OpenAI 模型选择指南](https://learn.chatgpt.com/docs/model-selection) · [强度、Max 和 Ultra](https://learn.chatgpt.com/docs/models) · [Standard、Fast 与 Ultrafast](https://learn.chatgpt.com/docs/agent-configuration/speed)

## 选择入口和自动化边界

- 普通 Chat 使用输入框附近的模型/思考档位菜单。Work 和 Codex 桌面用输入框的模型与强度控件；遇到 Power 滑杆可查看 Advanced。Codex CLI 用 `/model`，IDE 扩展用输入框附近的选择器。切换后发一条「已切换」即可；保留原会话时可以沿用现有上下文。 [ChatGPT 模型](https://help.openai.com/en/articles/20001354-gpt-6-and-other-models-in-chatgpt) · [Work/Codex 选择器](https://learn.chatgpt.com/docs/models)
- 自己开发的 Codex 客户端可用 App Server 的 `model/list` 读取支持的模型和强度，再由客户端为后续 `turn/start` 设置模型和强度。该能力属于接入这些接口的客户端。此项目提供工作流指令，自动应用取决于当前宿主是否公开提供相应能力。 [App Server](https://learn.chatgpt.com/docs/app-server)

## 额度、上下文与复核

- 截至核对日，Work 与 Codex 共享相应的订阅用量。Plus 等适用套餐中，5 小时与周窗口同时约束用量，两者的重置时间可能不同。以账号的 Settings → Usage（有的界面为 Usage & billing）为准；Codex CLI 可用 `/status` 查看可用信息。任务规模、上下文、模型及速度设置都会影响使用量。 [用量与价格](https://learn.chatgpt.com/docs/pricing) · [Codex 重置机制](https://help.openai.com/en/articles/20001498-how-resets-work-in-codex)
- OpenAI 已预告从 2026 年 12 月起在 Plus、Pro、Business 上把 ChatGPT 与 Codex 的用量合并计量，并注明 Instant chat 不计入该共享用量。处于过渡期时，以账户显示和最新公告为准。 [共享用量公告](https://help.openai.com/en/articles/20001625-understanding-chatgpt-and-codex-usage-limits)
- 保留正在用的证据、文件路径和关键决策；阶段交接用短摘要，避免重复粘贴整段对话和无关附件。批量处理前先取小样核对规则，再确定是否值得整批执行。对于正在推进的复杂工作，可在当前对话切换时沿用必要上下文。评估实际节省时，比较达到同一质量所花的总用量、时间和人工返工。 [用量因素](https://learn.chatgpt.com/docs/pricing) · [比较配置](https://learn.chatgpt.com/docs/model-selection)
