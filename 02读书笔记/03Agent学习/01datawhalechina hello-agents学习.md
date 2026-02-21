# datawhalechina hello-agents学习

> 创建：2026.2.20
> 资源链接：https://github.com/datawhalechina/hello-agents/blob/main/README.md


---

## 🎯 项目介绍

&emsp;&emsp;如果说 **2024 年是"百模大战"的元年，那么 2025 年无疑开启了"Agent 元年"。** 技术的焦点正从训练更大的基础模型，转向构建更聪明的智能体应用。然而，当前系统性、重实践的教程却极度匮乏。为此，我们发起了 Hello-Agents 项目，希望能为社区提供一本从零开始、理论与实战并重的智能体系统构建指南。

&emsp;&emsp;Hello-Agents 是 Datawhale 社区的`<strong>`系统性智能体学习教程`</strong>`。如今 Agent 构建主要分为两派，一派是 Dify，Coze，n8n 这类**软件工程类 Agent，本质是流程驱动的软件开发，LLM 作为数据处理的后端；** 另一派则是 **AI 原生的 Agent，即真正以 AI 驱动的 Agent。** 本教程旨在带领大家深入理解并构建后者——真正的 AI Native Agent。教程将带领你穿透框架表象，从智能体的核心原理出发，深入其核心架构，理解其经典范式，并最终亲手构建起属于自己的多智能体应用。我们相信，最好的学习方式就是动手实践。希望这本教程能成为你探索智能体世界的起点，能够从一名大语言模型的"使用者"，蜕变为一名智能体系统的"构建者"。

## 📚 快速开始

### 在线阅读

**[🌐 点击这里开始在线阅读](https://datawhalechina.github.io/hello-agents/)** - 无需下载，随时随地学习

**[📖 Cookbook](https://book.heterocat.com.cn/)**

### ✨ 你将收获什么？

- 📖 `<strong>`Datawhale 开源免费`</strong>` 完全免费学习本项目所有内容，与社区共同成长
- 🔍 `<strong>`理解核心原理`</strong>` 深入理解智能体的概念、历史与经典范式
- 🏗️ `<strong>`亲手实现`</strong>` 掌握热门低代码平台和智能体代码框架的使用
- 🛠️ `<strong>`自研框架[HelloAgents](https://github.com/jjyaoao/helloagents)`</strong>` 基于 Openai 原生 API 从零构建一个自己的智能体框架
- ⚙️ `<strong>`掌握高级技能`</strong>` 一步步实现上下文工程、Memory、协议、评估等系统性技术
- 🤝 `<strong>`模型训练`</strong>` 掌握 Agentic RL，从 SFT 到 GRPO 的全流程实战训练 LLM
- 🚀 `<strong>`驱动真实案例`</strong>` 实战开发智能旅行助手、赛博小镇等综合项目
- 📖 `<strong>`求职面试`</strong>` 学习智能体求职相关面试问题

## 📖 内容导航

| 章节                                                                                     | 关键内容                                      | 状态 |
| ---------------------------------------------------------------------------------------- | --------------------------------------------- | ---- |
| [前言](./docs/前言.md)                                                                      | 项目的缘起、背景及读者建议                    | ✅   |
| `<strong>`第一部分：智能体与语言模型基础`</strong>`                                  |                                               |      |
| [第一章 初识智能体](./docs/chapter1/第一章%20初识智能体.md)                                 | 智能体定义、类型、范式与应用                  | ✅   |
| [第二章 智能体发展史](./docs/chapter2/第二章%20智能体发展史.md)                             | 从符号主义到 LLM 驱动的智能体演进             | ✅   |
| [第三章 大语言模型基础](./docs/chapter3/第三章%20大语言模型基础.md)                         | Transformer、提示、主流 LLM 及其局限          | ✅   |
| `<strong>`第二部分：构建你的大语言模型智能体`</strong>`                              |                                               |      |
| [第四章 智能体经典范式构建](./docs/chapter4/第四章%20智能体经典范式构建.md)                 | 手把手实现 ReAct、Plan-and-Solve、Reflection  | ✅   |
| [第五章 基于低代码平台的智能体搭建](./docs/chapter5/第五章%20基于低代码平台的智能体搭建.md) | 了解 Coze、Dify、n8n 等低代码智能体平台使用   | ✅   |
| [第六章 框架开发实践](./docs/chapter6/第六章%20框架开发实践.md)                             | AutoGen、AgentScope、LangGraph 等主流框架应用 | ✅   |
| [第七章 构建你的Agent框架](./docs/chapter7/第七章%20构建你的Agent框架.md)                   | 从 0 开始构建智能体框架                       | ✅   |
| `<strong>`第三部分：高级知识扩展`</strong>`                                          |                                               |      |
| [第八章 记忆与检索](./docs/chapter8/第八章%20记忆与检索.md)                                 | 记忆系统，RAG，存储                           | ✅   |
| [第九章 上下文工程](./docs/chapter9/第九章%20上下文工程.md)                                 | 持续交互的"情境理解"                          | ✅   |
| [第十章 智能体通信协议](./docs/chapter10/第十章%20智能体通信协议.md)                        | MCP、A2A、ANP 等协议解析                      | ✅   |
| [第十一章 Agentic-RL](./docs/chapter11/第十一章%20Agentic-RL.md)                            | 从 SFT 到 GRPO 的 LLM 训练实战                | ✅   |
| [第十二章 智能体性能评估](./docs/chapter12/第十二章%20智能体性能评估.md)                    | 核心指标、基准测试与评估框架                  | ✅   |
| `<strong>`第四部分：综合案例进阶`</strong>`                                          |                                               |      |
| [第十三章 智能旅行助手](./docs/chapter13/第十三章%20智能旅行助手.md)                        | MCP 与多智能体协作的真实世界应用              | ✅   |
| [第十四章 自动化深度研究智能体](./docs/chapter14/第十四章%20自动化深度研究智能体.md)        | DeepResearch Agent 复现与解析                 | ✅   |
| [第十五章 构建赛博小镇](./docs/chapter15/第十五章%20构建赛博小镇.md)                        | Agent 与游戏的结合，模拟社会动态              | ✅   |
| `<strong>`第五部分：毕业设计及未来展望`</strong>`                                    |                                               |      |
| [第十六章 毕业设计](./docs/chapter16/第十六章%20毕业设计.md)                                | 构建属于你的完整多智能体应用                  | ✅   |

### 社区贡献精选 (Community Blog)

&emsp;&emsp;欢迎大家将在学习 Hello-Agents 或 Agent 相关技术中的独到见解、实践总结，以 PR 的形式贡献到社区精选。如果是独立于正文的内容，也可以投稿至 Extra-Chapter！`<strong>`期待你的第一次贡献！`</strong>`

| 社区精选                                                                                                                                   | 内容总结                  |
| ------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------- |
| [00-共创毕业设计](https://github.com/datawhalechina/hello-agents/blob/main/Co-creation-projects)                                              | 社区共创毕业设计项目      |
| [01-Agent面试题总结](https://github.com/datawhalechina/hello-agents/blob/main/Extra-Chapter/Extra01-面试问题总结.md)                          | Agent 岗位相关面试问题    |
| [01-Agent面试题答案](https://github.com/datawhalechina/hello-agents/blob/main/Extra-Chapter/Extra01-参考答案.md)                              | 相关面试问题答案          |
| [02-上下文工程内容补充](https://github.com/datawhalechina/hello-agents/blob/main/Extra-Chapter/Extra02-上下文工程补充知识.md)                 | 上下文工程内容扩展        |
| [03-Dify智能体创建保姆级教程](https://github.com/datawhalechina/hello-agents/blob/main/Extra-Chapter/Extra03-Dify智能体创建保姆级操作流程.md) | Dify智能体创建保姆级教程  |
| [04-Hello-agents课程常见问题](https://github.com/datawhalechina/hello-agents/blob/main/Extra-Chapter/Extra04-DatawhaleFAQ.md)                 | Datawhale课程常见问题     |
| [05-Agent Skills与MCP对比解读](https://github.com/datawhalechina/hello-agents/blob/main/Extra-Chapter/Extra05-AgentSkills解读.md)             | Agent Skills与MCP技术对比 |
| [06-GUI Agent科普与实战](https://github.com/datawhalechina/hello-agents/blob/main/Extra-Chapter/Extra06-GUIAgent科普与实战.md)                | GUI Agent科普与多场景实战 |
| [07-环境配置](https://github.com/datawhalechina/hello-agents/blob/main/Extra-Chapter/Extra07-环境配置.md)                                     | 环境配置                  |

### PDF 版本下载

> *Hello-Agents PDF : https://github.com/datawhalechina/hello-agents/releases/tag/V1.0.0*
> *Hello-Agents PDF 国内下载地址 : https://www.datawhale.cn/learn/summary/239*

## 💡 如何学习

&emsp;&emsp;欢迎你，未来的智能系统构建者！在开启这段激动人心的旅程之前，请允许我们给你一些清晰的指引。

&emsp;&emsp;本项目内容兼顾理论与实战，旨在帮助你系统性地掌握从单个智能体到多智能体系统的设计与开发全流程。因此，尤其适合有一定编程基础的 `<strong>`AI 开发者、软件工程师、在校学生`</strong>` 以及对前沿 AI 技术抱有浓厚兴趣的 `<strong>`自学者`</strong>`。在学习本项目之前，我们希望你具备基础的 Python 编程能力，并对大语言模型有基本的概念性了解（例如，知道如何通过 API 调用一个 LLM）。项目的重点是应用与构建，因此你无需具备深厚的算法或模型训练背景。

&emsp;&emsp;项目分为五大部分，每一部分都是通往下一阶段的坚实阶梯：

- `<strong>`第一部分：智能体与语言模型基础`</strong>`（第一章～第三章），我们将从智能体的定义、类型与发展历史讲起，为你梳理"智能体"这一概念的来龙去脉。随后，我们会快速巩固大语言模型的核心知识，为你的实践之旅打下坚实的理论地基。
- `<strong>`第二部分：构建你的大语言模型智能体`</strong>`（第四章～第七章），这是你动手实践的起点。你将亲手实现 ReAct 等经典范式，体验 Coze 等低代码平台的便捷，并掌握 Langgraph 等主流框架的应用。最终，我们还会带你从零开始构建一个属于自己的智能体框架，让你兼具“用轮子”与“造轮子”的能力。
- `<strong>`第三部分：高级知识扩展`</strong>`（第八章～第十二章），在这一部分，你的智能体将“学会”思考与协作。我们将使用第二部分的自研框架，深入探索记忆与检索、上下文工程、Agent 训练等核心技术，并学习多智能体间的通信协议。最终，你将掌握评估智能体系统性能的专业方法。
- `<strong>`第四部分：综合案例进阶`</strong>`（第十三章～第十五章），这里是理论与实践的交汇点。你将把所学融会贯通，亲手打造智能旅行助手、自动化深度研究智能体，乃至一个模拟社会动态的赛博小镇，在真实有趣的项目中淬炼你的构建能力。
- `<strong>`第五部分：毕业设计及未来展望`</strong>`（第十六章），在旅程的终点，你将迎来一个毕业设计，构建一个完整的、属于你自己的多智能体应用，全面检验你的学习成果。我们还将与你一同展望智能体的未来，探索激动人心的前沿方向。

&emsp;&emsp;智能体是一个飞速发展且极度依赖实践的领域。为了获得最佳的学习效果，我们在项目的 `code`文件夹内提供了配套的全部代码，强烈建议你`<strong>`将理论与实践相结合`</strong>`。请务必亲手运行、调试甚至修改项目里提供的每一份代码。欢迎你随时关注 Datawhale 以及其他 Agent 相关社区，当遇到问题时，你可以随时在本项目的 issue 区提问。
