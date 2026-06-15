# docker desktop学习
> 2026.6.12

## 1 Docker简介
   Docker 是一个开源的应用容器引擎，是一组平台即服务（PaaS）的产品，它基于操作系统层级的虚拟化技术，将软件与其依赖项打包为容器。托管容器的软件称为Docker引擎。Docker能够帮助开发者在轻量级容器中自动部署应用程序，并使得不同容器中的应用程序彼此隔离，高效工作。

   Docker分为CE（Community Edition: 社区版） 和 EE（Enterprise Edition: 企业版）。

### 1.1. 核心概念
- 镜像是容器的模板，容器是镜像的实例；
- 数据卷挂载在容器上，其数据不随容器删除而丢失；
- 网络是容器与宿主机、容器之间互联的桥梁；
#### 1.1.1镜像 (Image)
- 定义：镜像是一个只读的模板，包含了运行应用所需的所有内容：代码、运行时、库文件、环境变量和配置文件。
- 特点：
  - 分层存储：镜像由多个层组成，每一层代表一次修改
  - 只读性：镜像本身是只读的，不能直接修改
  - 可复用：同一个镜像可以创建多个容器
  - 版本管理：通过标签(tag)进行版本管理
  类比理解：镜像就像是一个安装程序或者模板，它定义了应用运行所需的一切，但本身不能直接运行。

#### 1.1.2容器 (Container)
- 定义：容器是镜像的运行实例，是一个轻量级、可移植的执行环境。
- 特点：
  - 隔离性：每个容器都有自己的文件系统、网络和进程空间
  - 临时性：容器可以被创建、启动、停止、删除
  - 可写层：容器在镜像基础上添加了一个可写层
  - 进程级：容器内通常运行一个主进程
  类比理解：如果镜像是类，那么容器就是对象实例。一个镜像可以创建多个容器，就像一个类可以创建多个对象。

#### 1.1.3存储
docker存储的两种方式：volume卷和bind mount绑定挂载，容器不存在时存储数据仍在，可实现数据持久化存储。
卷由Docker管理，并且与主机的核心功能隔离。卷比绑定挂载更容易备份、迁移，性能更高，还可以加密。
绑定挂载将主机上的文件或目录挂载到docker容器中。
##### 1.1.3.1 volume卷
显式创建卷：`docker volume create 卷名`
卷可以同时安装到多个容器中，实现容器间的数据共享；
卷有助于将 Docker 主机的配置与容器运行时分离。
卷可以将容器的数据存储在远程主机或云提供商上；

##### 1.1.3.2 bind mount绑定挂载



#### 1.1.4网络 (Network)
容器只能看到一个具有 IP 地址、网关、路由表、DNS 服务和其他网络细节的网络接口。
- docker容器间组网：
  - 创建用户自定义网络`docker network create -d bridge my-net`，可将多个容器连接到同一个网络，容器之间可以使用容器 IP 地址或容器名称相互通信。
  - 容器间通信：通过将容器连接到同一网络（通常是 `桥接网络`）即可。
  - 容器接入网络：创建容器时用`--network network_name`入网；已运行的容器使用`docker network connect network_name container_name`命令，将正在运行的容器连接到指定的网络。

- 容器网络连接方式：[详见……](https://docs.docker.top/engine/network/drivers/index.htm)
  - bridge：默认网络驱动程序，不支持跨docker主机之间的网络通信（区别于overlay）。
    - 使用场景：在同一个docker主机上，接入同一个桥接网络的容器，容器之间可以实现网络通信，网络隔离未连接到该桥接网络的容器。
    - 网络安全策略：Docker为bridge创建 `iptables` 和 `ip6tables` 规则，防止未经授权访问容器或主机上运行的其他服务，从而实现网络隔离、端口发布和过滤。[详见 `数据包过滤和防火墙`……](https://docs.docker.top/engine/network/packet-filtering-firewalls/index.htm)
    - 默认桥接网络

    - 用户自定义桥接网络：

    - 桥接网络的连接限制：由于Linux内核设置的限制，当1000个或更多容器连接到单个网络时，桥接网络会变得不稳定，容器间通信可能会中断。



  - host：删除容器和 Docker 主机之间的网络隔离，容器直接使用主机的网络和80端口，即通过主机的localhost：80即可访问容器，容器没有自己的IP地址。
  - none：将容器与主机和其他容器完全隔离。
  - overlay：将多个 Docker 守护程序连接在一起，并使Swarm服务和容器能够跨节点进行通信，消除了进行操作系统级路由的需要。
    - 使用场景：跨docker主机的多个容器需要通信，或者多个应用程序使用Swarm服务协同工作时；
  - ipvlan：完全控制IPv4和IPv6寻址。
  - macvlan：为容器分配 MAC 地址，Docker守护程序通过容器的MAC地址将流量路由到容器。

- 容器网络端口
  - 发布容器端口默认情况下对 Docker 主机和对外部世界都可用，故不安全；
  - 如果在发布标志中包含 localhost IP 地址（`127.0.0.1` 或 `::1`），则只有 Docker 主机及其容器可以访问已发布的容器端口。  

- 容器的ip地址：Docker守护程序会为容器执行动态子网划分和IP地址分配，每个网络具有默认子网掩码和网关。  
- 容器的主机名：默认为Docker中的容器ID，可以使用--hostname覆盖主机名。
- 容器DNS：
  - 容器默认使用与docker主机相同的DNS服务器；
  - 连接到 自定义网络 的容器使用Docker的嵌入式DNS服务器，嵌入式DNS服务器将外部DNS查找转发到主机上配置的DNS服务器。

#### 1.1.5仓库 (Repository)
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
    - 中文版：https://docs.docker.top/manuals/index.htm（分为入门、指南、手册、参考）
    - 英文版：https://docs.docker.com/get-started/get-docker

## 2 docker配置
docker build调用Dockerfile镜像构建文本文件（内含构建镜像所需的指令和说明），创建镜像image，可上传到仓库注册服务器Registry，存储在仓库Repository中；
docker compose调用yml容器构建文本文件（内含构建容器所需的指令和说明），创建容器container；
### 2.1 docker desktop配置
上网代理proxy
docker中的容器（例如vs code server）要与国外网站（例如github）同步，需要配置上网代理proxy。
`注：proxy安装在宿主机host上，docker软件、docker容器需分别设置，才能使用宿主机host的proxy。`
- docker软件上网代理proxy配置

- docker容器上网代理proxy配置
  proxy配置好后，新建的容器可以直接使用代理；之前已创建的容器，必须重新创建，才能是容器的proxy生效。

### 2.2 镜像配置和创建（Docker build Dockfile）

### 2.3 容器配置和创建（Docker compose yml）

## 3 docker使用
docker既可以当作虚拟机管理平台，也可以当作云平台，每个容器当作一台虚拟机，volume数据卷当作存储服务器，network当作虚拟网络。
可以在docker容器中部署windows、Linux等，把docker当作服务器资源池，可以建立集群管理节点、工作节点，每个工作节点对应一个容器，可以组网（本地组网、云端和本地联网等）

可以根据容器的inpsect信息，让LLM转写成yml格式的容器配置文件；


### 3.1 docker下载镜像、安装容器


## 4 docker常用命令
docker命令大全：https://www.runoob.com/docker/docker-command-manual.html
### 4.1 容器常用命令


### 4.2 镜像常用命令


### 4.3 存储常用命令


### 4.4 网络常用命令


### 4.5 Docker Dockfile常用命令


### 4.6 Docker Compose常用命令
