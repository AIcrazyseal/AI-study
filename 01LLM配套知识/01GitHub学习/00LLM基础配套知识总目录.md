# LLM基础配套知识总目录
> 2026.6.9

LLM的网上教程大体分为官方英文/中文文档、国内高手整理的学习文档两类。

**官方文档：** 权威、全面，但重点不突出、英文难懂、操作性稍差，是系统、全面学习和理解必由之路；

**国内高手整理的学习文档：** 操作性强、经过国内实践检验、易于理解，便于快速入门。

建议：先学国内高手整理的文档，实践落地调通，以便快速入门；想进一步深入学习时，再系统学习官方文档。

## 1 基础运行环境
LLM基础运行环境包括Linux虚拟环境、Docker容器环境。

### 1.1 Linux虚拟环境搭建
  在windows中安装WSL2（Windows Subsystem for Linux）和Ubuntu（Linux的一个版本），为容器Docker Desktop工具提供Linux运行环境。

  - Linux中文教程：https://www.runoob.com/linux/linux-tutorial.html（快速入门）

  - WSL2官方文档：https://learn.microsoft.com/zh-cn/windows/wsl/basic-commands（系统全面）
  
### 1.2 Docker容器环境搭建
  
  菜鸟教程：https://www.runoob.com/docker/docker-tutorial.html（快速入门）
           https://dockerdocs.xuanyuan.me/tutorial（轩辕）
  
  官方中文教程：https://docs.docker.top/get-started/index.htm（系统全面）

  官方英文教程：https://docs.docker.com/get-started/get-docker/（系统全面）
  
## 2 LLM各类资源

### 2.1 知识管理工具
github/

Watt Toolkit（网站加速工具）

### 2.2 LLM模型集市
以下网站是国内外知名的**集模型库、数据集、协作工具和社区于一体**网站，国内网站访问速度快，国外网站访问速度慢。

- 阿里巴巴的魔搭社区：http://www.modelscope.cn

- huggingface社区：国内https://hf-mirror.com 是国外网站 https://huggingface.co/ 的镜像网站。
  Spaces（AI应用空间/体验中心）汇集了大量基于Hugging Face模型的交互式AI应用Demo。可以：
    - 在线体验：无需配置环境，点几下就能玩转各种新奇AI应用。
    - 寻找灵感：看看别人都在用AI做什么好玩的事儿。
    - 学习与创造：很多Space也提供源代码，是学习和二次开发的好起点
  如何用好社区：https://zhuanlan.zhihu.com/p/1923227719933622255

- 轩辕镜像社区：https://xuanyuan.cloud

### 2.3常见AI学习资源
菜鸟教程（https://www.runoob.com/）

## 3 配套应用工具
### 3.1 LLM Models的运行环境  
  推荐使用llama.cpp，运行速度快，但学习成本稍高；ollama+Openwebui上手快，配置复杂，运行速度慢。
  - llama.cpp
  
  - ollama
  
  - Openwebui

  Agent编码、运行IDE：VS Code Server/Jupyter notebook

## 4 编程开发语言
  Markdown

  Python