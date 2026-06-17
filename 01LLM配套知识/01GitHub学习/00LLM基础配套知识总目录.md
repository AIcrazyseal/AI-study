# LLM基础配套知识总目录
> 2026.6.9

## 1 综述
### 1.1 LLM基础配套知识体系及关系
- 基础运行环境：
  - WSL2：Windows Subsystem for Linux，Windows系统中运行的Linux子系统，为docker提供Linux运行环境；

  - Docker Desktop：为LLM models、llama.cpp、Agent等提供逻辑隔离的容器，确保每个容器安装的软件、基础运行环境（lib库、扩展、环境变量等）独立，避免容器间因基础运行环境版本号不一样导致互相干扰，同时也不会污染宿主机host的环境；

- LLM models及管理工具
  - LLM models管理工具：llama.cpp/ollama+openwebui等，管理本地电脑上的models，可以通过ui界面直接与models对话，也可以通过API的方式为Agent提供服务；

  - LLM models：网上开源的AI模型，例如Qwen、GPT、llama、Deepseek等；

- LLM各类资源：
  - LLM模型集市：国内外可供下载的LLM models、数据集、API调用方法等；

  - github资源：学习知识存储在仓库中，与本地文件进行同步；github上有大量AI学习资源（文档、代码等）；

  - 国内优秀资源：阿里、腾讯、百度等官方AI开发资源中心，有大量优秀的AI学习文档；

- 编程开发工具及语言
  - vs code server：Agent开发的一体化IDE工具，可通过API调用llama.cpp的LLM model，与github同步可实现代码库管理；

  - Jupyter notebook：轻量级开发工具，易入门；

  - python和Markdown：AI开发常用语言，必学；

- 流行Agent框架：
  - hermes：Nous Research 推出的 Hermes Agent ，能自我学习、干活的agent，安全性比OpenClaw高；

  - OpenClaw：俗称“小龙虾”。

### 1.2 知识学习路径
LLM的网上教程大体分为官方英文/中文文档、国内高手整理的学习文档两类。

**官方文档：** 权威、全面，但重点不突出、英文难懂、操作性稍差，是系统、全面学习和理解必由之路；

**国内高手整理的学习文档：** 操作性强、经过国内实践检验、易于理解，便于快速入门。

建议：先学国内高手整理的文档，实践落地调通，以便快速入门；想进一步深入学习时，再系统学习官方文档。

## 2 基础运行环境
LLM基础运行环境包括Linux虚拟环境、Docker容器环境。

### 2.1 Linux虚拟环境搭建
  在windows中安装WSL2（Windows Subsystem for Linux）和Ubuntu（Linux的一个版本），为容器Docker Desktop工具提供Linux运行环境。

  - Linux中文教程：https://www.runoob.com/linux/linux-tutorial.html（快速入门）
  - WSL2官方文档：https://learn.microsoft.com/zh-cn/windows/wsl/basic-commands（系统全面）
  - [WSL学习笔记](01WSL学习.md)
  
### 2.2 Docker容器环境搭建
  Docker是一组平台即服务（PaaS）的产品，它基于操作系统层级的虚拟化技术，将软件与其依赖项打包为容器。托管容器的软件称为Docker引擎。Docker能够帮助开发者在轻量级容器中自动部署应用程序，并使得不同容器中的应用程序彼此隔离，高效工作。
  - 菜鸟教程：
    - https://www.runoob.com/docker/docker-tutorial.html（快速入门）
    - https://dockerdocs.xuanyuan.me/tutorial（轩辕）
  
  - 官方教程（系统全面）：
    - 中文版：https://docs.docker.top/get-started/index.htm
    - 英文版：https://docs.docker.com/get-started/get-docker
  
  - [docker学习笔记](02docker学习.md)
  
## 3 LLM Models及管理工具
  推荐使用llama.cpp，运行速度快，但学习成本稍高；ollama+Openwebui上手快，配置复杂，运行速度慢。

  - llama.cpp：模型管理工具（极简版Agent），实现模型下载，GUI界面选择和加载模型、模型对话，对外提供LLM model API调用链接；Agent开发学习推荐使用llama.cpp。
  
  - ollama：模型管理工具，是在llama.cpp上包装了一层，所以运行效率低于llama.cpp；docker容器中安装ollama，没有WebUI界面，必须配合Openwebui才能通过WebUI图形化界面实现模型下载、选择和对话；宿主机中直接安装ollama会有WebUI界面。
  
  - Openwebui：图形化的Agent，提供工具、函数等扩展插件，通过ollama调用LLM model，GUI界面可以选择和加载模型、模型对话、模型参数设置等，对外提供LLM model API调用链接；AI入门推荐此工具。
   
## 4 LLM国内外资源

### 4.1 LLM模型集市
以下网站是国内外知名的**集模型库、数据集、协作工具和社区于一体**网站，国内网站访问速度快，国外网站访问速度慢。

- 阿里巴巴的魔搭社区：http://www.modelscope.cn

- huggingface社区：国内https://hf-mirror.com 是国外网站 https://huggingface.co/ 的镜像网站。
  Spaces（AI应用空间/体验中心）汇集了大量基于Hugging Face模型的交互式AI应用Demo。可以：
    - 在线体验：无需配置环境，点几下就能玩转各种新奇AI应用。
    - 寻找灵感：看看别人都在用AI做什么好玩的事儿。
    - 学习与创造：很多Space也提供源代码，是学习和二次开发的好起点
  如何用好社区：https://zhuanlan.zhihu.com/p/1923227719933622255

- 轩辕镜像社区：https://xuanyuan.cloud

### 4.2常见AI学习资源
菜鸟教程（https://www.runoob.com/）

### 4.3 AI辅助工具

- github：是全球最大的‌代码托管平台‌和‌开发者协作社区‌，由微软旗下独立运营，核心基于 ‌Git‌ 版本控制系统，提供从代码存储、版本管理到自动化构建、安全扫描的一站式软件开发生命周期服务；‌‌此网站有丰富的AI学习资料、代码等。

- gitee：中国版github，是开源中国于 2013 年推出的基于Git的中国境内规模最大代码托管平台、企业级研发效能平台、一站式 DevSecOps 平台，提供中国本土化的代码托管和项目管理服务。

- Watt Toolkit：免费网页代理工具（VPN），主要用于国外网站加速，例如：github、huggingface等；
- Clash Verge Rev：免费网页代理工具；
  - [Clash Verge Rev网页代理github下载链接](https://github.com/clash-verge-rev/clash-verge-rev/releases)；
  - [Clash Verge Rev官方网站](www.clashverge.dev)
  - [使用教程](https://www.clashverge.dev/guide/quickstart.html#_1)

## 5 编程开发工具及语言
  - VS Code Server：Agent编码、运行IDE，功能强大，插件丰富，可与github同步，实现代码和知识的版本管理，企业级开发推荐使用，学习成本较高；
  
  - Jupyter notebook：轻量级Agent编码、运行IDE，配置简单，适合测试小功能，入门简单；

  - Markdown：轻量级标记语言，LLM model和Agent大量使用，是学习LLM的必要基础知识；

  - Python：解释型脚本语言，语法简洁，大量应用在AI开发中。

## 6 Agent开发框架
### 6.1 hermes
由Nous Research开发的一款开源自主AI智能体，专为持久运行和自我成长设计，通过FTS5检索技术实现跨会话记忆，并能自主创建程序化技能。用于搭建多Agent系统，涉及规划者、执行者和审核者角色，并集成了MCP（模型上下文协议）以扩展能力范围。
- 入门介绍：https://www.feishu.cn/content/article/7628541877674953666
- 官方文档：https://hermes-agent.ac.cn/docs
- github仓库：https://github.com/NousResearch/hermes-agent/blob/main/README.zh-CN.md

### 6.2 OpenClaw  
OpenClaw 是一个自托管 Gateway 网关，它把你常用的聊天应用和渠道界面（包括内置渠道，以及 Discord、Google Chat、iMessage、Matrix、Microsoft Teams、Signal、Slack、Telegram、WhatsApp、Zalo 等捆绑或外部渠道插件）连接到 Pi 等 AI 编码智能体。你在自己的机器（或服务器）上运行单个 Gateway 网关进程，它就会成为你的消息应用和始终可用的 AI 助手之间的桥梁。
- 官方文档：https://docs.openclaw.ai/zh-CN
- 官方博客：https://openclaw.ai/blog
