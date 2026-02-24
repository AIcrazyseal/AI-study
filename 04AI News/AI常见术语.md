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

1.requests

* 是 Python 社区最流行的 HTTP 库，用于发送网络请求\
* 功能：获取网页内容、调用 API、下载文件等\
* 示例用途：爬虫、与Web服务交互\
* [官方API文档链接](https://requests.readthedocs.io/en/latest/api/)

2.tavily-python

* 一个强大的 AI 搜索 API 客户端，Tavily 搜索引擎的 Python 客户端\
* 用于获取实时的网络搜索结果，可以在官网注册后获取 API。\
* 功能：专门为 AI 应用优化的搜索 API\
* 特点：提供实时、准确的搜索结果，适合构建 RAG（检索增强生成）应用
* [官方API文档链接](https://docs.tavily.com/sdk/python/quick-start)

3.openai

* OpenAI 官方提供的 Python SDK\
* 功能：调用 OpenAI 的 API 服务\
* 用途：使用 GPT 模型、Whisper（语音识别）、DALL-E（图像生成）等

