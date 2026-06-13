# docker desktop学习
> 2026.6.12

## 1 Docker简介
   Docker 是一个开源的应用容器引擎，是一组平台即服务（PaaS）的产品，它基于操作系统层级的虚拟化技术，将软件与其依赖项打包为容器。托管容器的软件称为Docker引擎。Docker能够帮助开发者在轻量级容器中自动部署应用程序，并使得不同容器中的应用程序彼此隔离，高效工作。

   Docker分为CE（Community Edition: 社区版） 和 EE（Enterprise Edition: 企业版）。

### 1.1. 核心概念
#### 1.1.1.1镜像 (Image)
- 定义：镜像是一个只读的模板，包含了运行应用所需的所有内容：代码、运行时、库文件、环境变量和配置文件。
- 特点：
  - 分层存储：镜像由多个层组成，每一层代表一次修改
  - 只读性：镜像本身是只读的，不能直接修改
  - 可复用：同一个镜像可以创建多个容器
  - 版本管理：通过标签(tag)进行版本管理
  类比理解：镜像就像是一个安装程序或者模板，它定义了应用运行所需的一切，但本身不能直接运行。

#### 1.1.1.2容器 (Container)
- 定义：容器是镜像的运行实例，是一个轻量级、可移植的执行环境。
- 特点：
  - 隔离性：每个容器都有自己的文件系统、网络和进程空间
  - 临时性：容器可以被创建、启动、停止、删除
  - 可写层：容器在镜像基础上添加了一个可写层
  - 进程级：容器内通常运行一个主进程
  类比理解：如果镜像是类，那么容器就是对象实例。一个镜像可以创建多个容器，就像一个类可以创建多个对象。

#### 1.1.1.3仓库 (Repository)
- 定义：仓库是存储和分发镜像的地方，可以包含一个镜像的多个版本。
- 分类：
  - 公共仓库：如 Docker Hub，任何人都可以使用
  - 私有仓库：企业内部搭建，用于存储私有镜像
  - 官方仓库：由软件官方维护的镜像仓库
- Registry vs Repository：
  - Registry：仓库注册服务器，如 Docker Hub
  - Repository：具体的镜像仓库，如 nginx、mysql

### 1.2 docker架构组件
- Docker是C/S架构，Docker 客户端与 Docker daemon守护进程通信，Docker daemon守护进程与docker regiestry就镜像、扩展和插件进行交互。
- Docker Desktop由以下模块构成：
  - Docker Engine：由Docker Client + Docker Daemon + REST API组成，是Docker的核心组件
  - Docker CLI客户端：用户与Docker交互的主要方式，接收用户命令并发送给本地或远程Docker Daemon
  - Docker Daemon守护进程：是Docker的核心服务进程，管理镜像、容器、网络和存储卷，监听Docker API请求并处理
  - Docker Registry（docker hub）：存储和分发Docker镜像，提供镜像的版本管理，支持公有和私有仓库
  - Docker Scout（可能需要额外订阅）
  - Docker Build
  - Docker扩展
  - Docker Compose
  - Docker内容信任
  - Kubernetes
  - 凭据助手

### 1.3 学习资源
  
  - 菜鸟教程：
    - https://www.runoob.com/docker/docker-tutorial.html（快速入门）
    - https://dockerdocs.xuanyuan.me/tutorial（轩辕）
  
  - 官方教程（系统全面）：
    - 中文版：https://docs.docker.top/get-started/index.htm（分为入门、指南、手册、参考）
    - 英文版：https://docs.docker.com/get-started/get-docker

## 2 docker安装


## 3 docker配置

### 3.1 docker 下载镜像、安装容器

### 3.2 docker配置上网代理proxy
docker中的容器（例如vs code server）要与国外网站（例如github）同步，需要配置上网代理proxy。
`注：proxy安装在宿主机host上，docker软件、docker容器需分别设置，才能使用宿主机host的proxy。`
- docker软件上网代理proxy配置

- docker容器上网代理proxy配置
  proxy配置好后，新建的容器可以直接使用代理；之前已创建的容器，必须重新创建，才能是容器的proxy生效。

## 4 docker常用命令
