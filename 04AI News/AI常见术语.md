# AI常见专业术语

> 创建：2026.2.22

1.大模型常见概念

* LLM(大语言模型):用于生成与理解文本
* Prompt：给LLM的指令，用于生成结果
* Embedding(向量嵌入)：文本向量化，支持检索与相似度判断
* RAG：增强检索生成，让模型带知识回答
* fine-tuning：针对特定任务微调训练好的通用模型，以提高通用模型在垂直专用领域的表现
* LoRA：低成本LLM微调方式，参数更小、速度更快
* Function Calling：让模型调用外部工具、接口
* Agent：能自主拆解任务、执行步骤的智能体
* Vector DB：存储向量数据，用于检索、知识库构建
* Tokenizer(分词器)：，把文本切成token，供模型理解
* Chain-of-thought：让模型展示推理步骤，提高LLM逻辑能力
* System Prompt：设定模型角色与行为规则的系统指令
* API Key：调用模型服务的身份凭证
* Sampling：控制模型随机度（top-p，temperature）
* RLHF：用人类反馈优化模型表现
* DPO：新型对齐方式，替代RLHF
* Checkpoint：模型权重文件，用于训练与部署

2.AI 编程辅助工具

- **GitHubCopilot** : 作为该领域最具影响力的产品之一，Copilot 由 GitHub 与 OpenAI 联合开发。它深度集成于 Visual Studio Code 等主流编辑器中，以其强大的**代码自动补全**能力而闻名。开发者在编写代码时，Copilot 能实时提供整行甚至整个函数块的建议。近年来，它也通过 **Copilot Chat 扩展了对话式编程的能力**，允许开发者在编辑器内通过聊天解决编程问题。copilot免费，copilot Pro和Pro+收费。[中文官方学习文档](https://code.visualstudio.com/docs/copilot/overview)
- **Claude Code** : Claude Code 是由 Anthropic 开发的 **AI 编程助手**，旨在**通过自然语言指令**帮助开发者在终端中高效地**完成编码任务**。它能够理解完整的代码库结构，执行代码编辑、测试和调试等操作，支持从描述功能到代码实现的全流程开发。Claude Code 还提供了无交互（headless）模式，适用于 CI、pre-commit hooks、构建脚本和其他自动化场景，为开发者提供了强大的命令行编程体验。
- **Trae** : 作为新兴的 **AI 编程工具**，Trae 专注于为开发者**提供智能化的代码生成和优化服务**。它通过深度学习技术分析代码模式，能够为开发者**提供精准的代码建议和自动化重构方案**。Trae 的特色在于其**轻量级的设计和快速响应能力，特别适合需要频繁迭代和快速原型开发的场景**。[中文学习文档](https://docs.trae.cn/ide/what-is-trae?_lang=zh)
- **Cursor** : 与上述主要作为插件或集成功能存在的工具不同，Cursor 则选择了一条更具整合性的路径，它本身就是一个 **AI 原生的代码编辑器**。它并非在现有编辑器上增加 AI 功能，而是在设计之初就**将 AI 交互作为核心**。除了**具备顶级的代码生成和聊天能力**外，它更强调让 **AI 理解整个代码库的上下文**，从而**实现更深层次的问答、重构和调试**。

2.requests

* 是 Python 社区最流行的 HTTP 库，用于发送网络请求\
* 功能：获取网页内容、调用 API、下载文件等\
* 示例用途：爬虫、与Web服务交互\
* [官方API文档链接](https://requests.readthedocs.io/en/latest/api/)

3.tavily-python

* 一个强大的 AI 搜索 API 客户端，Tavily 搜索引擎的 Python 客户端\
* 用于获取实时的网络搜索结果，可以在官网注册后获取 API。\
* 功能：专门为 AI 应用优化的搜索 API\
* 特点：提供实时、准确的搜索结果，适合构建 RAG（检索增强生成）应用
* [官方API文档链接](https://docs.tavily.com/sdk/python/quick-start)

4.openai

* OpenAI 官方提供的 Python SDK\
* 功能：调用 OpenAI 的 API 服务\
* 用途：使用 GPT 模型、Whisper（语音识别）、DALL-E（图像生成）等
