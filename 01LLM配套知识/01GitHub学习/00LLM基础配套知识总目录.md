# LLM基础配套知识总目录
> 2026.6.9

## 1 综述
### 1.1 LLM基础配套知识体系及关系
- 基础运行环境：
  - **WSL2**：为docker提供Linux运行环境；

  - **Docker Desktop**：为LLM models、llama.cpp、Agent等提供逻辑隔离的容器，确保每个容器安装的软件、基础运行环境（lib库、扩展、环境变量等）独立，避免容器间因基础运行环境版本号不一样导致互相干扰，同时也不会污染宿主机host的环境；

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

  - python和Markdown：AI开发常用语言；

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
  
### 2.2 Docker容器环境搭建
  
  菜鸟教程：https://www.runoob.com/docker/docker-tutorial.html（快速入门）
           https://dockerdocs.xuanyuan.me/tutorial（轩辕）
  
  官方中文教程：https://docs.docker.top/get-started/index.htm（系统全面）

  官方英文教程：https://docs.docker.com/get-started/get-docker/（系统全面）
  
  docker典型配置：
  
## 3 LLM Models及管理工具
### 3.1   
  推荐使用llama.cpp，运行速度快，但学习成本稍高；ollama+Openwebui上手快，配置复杂，运行速度慢。
  - llama.cpp
  
  - ollama
  
  - Openwebui

  
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

### 4.3 知识管理工具
github/

Watt Toolkit（网站加速工具）





## 5 编程开发工具及语言
  Agent编码、运行IDE：VS Code Server/Jupyter notebook

  Markdown

  Python

## 6 Agent开发框架
### 6.1 hermes
- 入门介绍：https://www.feishu.cn/content/article/7628541877674953666
- 官方文档：

### 6.2 OpenClaw  