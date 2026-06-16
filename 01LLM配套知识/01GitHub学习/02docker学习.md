# docker desktop学习
> 2026.6.12

## 1 Docker介绍
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
docker存储的两种方式：volume卷和bind mount绑定挂载，当删除容器时存储数据仍在，可实现数据持久化存储。
卷由Docker管理，并且与主机的核心功能隔离。卷比绑定挂载更容易备份、迁移，性能更高，还可以加密。
绑定挂载将主机上的文件或目录挂载到docker容器中。
##### 1.1.3.1 volume卷
卷由Docker创建和管理，存储在Docker主机上的目录中，与docker主机的核心功能隔离。

卷可以同时安装到多个容器中，卷的内容可以授权容器读写，实现容器间的数据共享；

使用卷驱动程序，卷可以将数据存储在远程主机或云提供商上；

卷是首选的持久化 Docker 容器和服务中的数据的方式。

卷有助于将 Docker 主机的配置与容器运行时分离。

- 常用命令
  - 显式创建卷：`docker volume create 卷名`
  - 列出现有卷：`docker volume ls`
  - 查看卷信息：`docker volume inspect 卷名`   #创建卷后，可以用inpsect检查卷是否配置正确
  - 删除卷：   `docker volume rm 卷名`
  - **-v/--volume参数说明**：`-v volume_name:destination_path:ro/rw`
    - volume_name:卷名
    - destination_path：卷要挂载到容器的文件夹位置
    - ro/rw:ro(readonly只读权限)，rw(read & write读写权限)
  - **--mount参数说明**：由多个键值对组成，用逗号分隔，每个键值对由一个<key>=<value>元组组成
    - 典型写法：`--mount 'type=volume,src=<VOLUME-NAME>,dst=<CONTAINER-PATH>,volume-driver=local,volume-opt=type=nfs,volume-opt=device=<nfs-server>:<nfs-path>,"volume-opt=o=addr=<nfs-address>,vers=4,soft,timeo=180,bg,tcp,rw"'
    - type:可以是bind、volume或tmpfs
    - src=<VOLUME-NAME>,命名卷src为卷名，匿名卷要省略src；
    - dest的值是文件或目录在容器中挂载的路径，destination、dst或target含义是等价的；
    - volume-subpath：指定要挂载到容器中的卷内子目录的路径，子目录必须存在于卷中；
  - **挂载卷子目录**：使用 --mount 标志的 volume-subpath。先新建卷，然后在卷下创建子目录，然后将卷的不同子目录挂载到不同的容器，实现不同容器的数据集中管理、各容器的数据相互隔离；示例如下：
      ```
      docker volume create logs
      docker run --rm \
        --mount src=logs,dst=/logs \
        alpine mkdir -p /logs/app1 /logs/app2
      docker run -d \
        --name=app1 \
        --mount src=logs,dst=/var/log/app1/,volume-subpath=app1 \
        app1:latest
      docker run -d \
        --name=app2 \
        --mount src=logs,dst=/var/log/app2,volume-subpath=app2 \
        app2:latest
      ```  
- 卷的驱动程序
  - 安装卷驱动插件（例如：vieux/sshfs）：`docker plugin install --grant-all-permissions vieux/sshfs`
  - 使用卷驱动程序创建卷
  - 启动使用卷驱动程序创建卷的容器

- 卷的备份、恢复、迁移数据卷、删除  



##### 1.1.3.2 bind mount绑定挂载
使用绑定挂载时，用主机上的文件或目录的绝对路径引用/挂载到容器中某个目录下。
相较于卷，无法使用 Docker CLI 命令直接管理绑定挂载。
- **-v/--volume参数说明**：`-v source_path:destination_path:ro/rw`
    - source_path:docker主机上文件或目录的路径。
    - destination_path：卷要挂载到容器的文件夹位置
    - ro/rw:ro(readonly只读权限)，rw(read & write读写权限)

- **--mount参数说明**：绑定挂载以只读的方式挂载到容器，volume的type:bind，其他参数含义与vulume的挂载一样；



#### 1.1.4网络 (Network)
容器只能看到一个具有 IP 地址、网关、路由表、DNS 服务和其他网络细节的网络接口。

- 容器网络连接方式：bridge、host、overlay、ipvlan、macvlan、none[详见……](https://docs.docker.top/engine/network/drivers/index.htm)
- docker容器间组网（同一docker主机的桥接bridge组网和跨docker主机的overlay组网）：
  - 创建用户自定义网络`docker network create -d bridge my-net`，可将多个容器连接到同一个网络，容器之间可以使用容器 IP 地址或容器名称相互通信。
  - 容器间通信：通过将容器连接到同一网络（通常是 `桥接网络`）即可。
  - 容器接入网络：创建容器时用`--network network_name`入网；已运行的容器使用`docker network connect network_name container_name`命令，将正在运行的容器连接到指定的网络。
- 容器网络端口
  - 发布容器端口默认情况下对 Docker 主机和对外部世界都可用，故不安全；
  - 如果在发布标志中包含 localhost IP 地址（`127.0.0.1` 或 `::1`），则只有 Docker 主机及其容器可以访问已发布的容器端口。  

- 容器的ip地址：Docker守护程序会为容器执行动态子网划分和IP地址分配，每个网络具有默认子网掩码和网关。  
- 容器的主机名：默认为Docker中的容器ID，可以使用--hostname覆盖主机名。
- 容器DNS：
  - 容器默认使用与docker主机相同的DNS服务器；
  - 连接到 自定义网络 的容器使用Docker的嵌入式DNS服务器，嵌入式DNS服务器将外部DNS查找转发到主机上配置的DNS服务器。

##### 1.1.4.1 bridge网络
是docker的默认网络驱动程序，不支持跨docker主机之间的网络通信（区别于overlay）。
- 使用场景：在同一个docker主机上，接入同一个桥接网络的容器，都可以访问其他容器公开的所有端口，网络隔离未连接到该桥接网络的容器。
- 网络安全策略：Docker为bridge创建 `iptables` 和 `ip6tables` 规则，防止未经授权访问容器或主机上运行的其他服务，从而实现网络隔离、端口发布和过滤。[详见 `数据包过滤和防火墙`……](https://docs.docker.top/engine/network/packet-filtering-firewalls/index.htm)
- 默认桥接网络(生产环境不推荐)
  - **创建和配置**：不可创建，只可配置；默认桥接网络的配置发生在Docker本身之外，修改配置需重启Docker访客生效；
  - **通信方式**：默认桥接网络上的容器只能通过IP地址相互访问；
  - **网络安全性**：所有未指定--network的容器都附加到默认桥接网络，容器间都可以通信，存在被无关容器访问的潜在网络风险；
  - **容器入网方式**：要从默认桥接网络中移除容器，您需要停止容器并使用不同的网络选项重新创建它。

- 用户自定义桥接网络（推荐这种网络方式）
  - **创建和配置**：`docker network create network_name`创建，可以配置网络信息；
  - **通信方式**：用户定义的桥接提供容器之间的自动DNS解析，容器间通过容器名或别名相互访问；
  - **网络安全性**：只有附加到用户自定义网络的容器才能相互通信；
  - **容器入网方式**：容器可以动态地附加到用户定义的网络和从用户定义的网络分离

- 用户自定义网络常用命令：
  - 创建网络：`docker network create network_name`;
  - 删除网络：`docker network rm network_name`;
  - 接入网络：创建新容器时，用`--network network_name`入网;已有容器入网用`docker network connect network_name container_name`
  - 断开网络：`docker network disconnect network_name container_name`

- 桥接网络的连接限制：由于Linux内核设置的限制，当1000个或更多容器连接到单个网络时，桥接网络会变得不稳定，容器间通信可能会中断。

##### 1.1.4.2 host网络  
host网络删除容器和 Docker 主机之间的网络隔离，容器直接使用主机的网络和80端口，即通过主机的localhost：80即可访问容器，容器没有自己的IP地址。

##### 1.1.4.3 overlay网络  
overlay网络在多个 Docker daemon 主机之间创建分布式网络，允许连接到overlay网络的容器进行加密通信。Docker 透明地处理从正确的 Docker daemon 主机到正确的目标容器的每个数据包的路由。
- 跨docker主机将多个 Docker 守护程序连接在一起，并使Swarm服务和容器能够跨节点进行通信，消除了进行操作系统级路由的需要。
- 使用场景：跨docker主机的多个容器需要通信，或者多个应用程序使用Swarm服务协同工作时；
- 参与 Overlay 网络的每个主机需要打开的端口
      |端口	| 描述 |
      |-----|-----|
      |2377/tcp	|默认 Swarm 控制平面端口，可以使用 `docker swarm join --listen-addr` 配置|
      |4789/udp	|默认 Overlay 流量端口，可以使用 `docker swarm init --data-path-addr` 配置|
      |7946/tcp, 7946/udp	|用于节点之间的通信，不可配置|
- 创建overlay网络：
      ```
      docker network create \            #创建docker网络
      --opt encrypted \                  #网络数据加密
      --driver overlay \                 #网络驱动为overlay
      --attachable \                     #使独立容器和 Swarm 服务都可以连接到 Overlay 网络
      my-attachable-multi-host-network   #overlay网络名
      ```
- 不要将 Windows 容器连接到加密的 Overlay 网络。Windows 不支持 Overlay 网络加密。当 Windows 主机尝试连接到加密的 Overlay 网络时，Swarm 不会报告错误，但 Windows 容器无法与网络上的 Linux 容器通信，网络上Windows容器之间的数据流量未加密  
- Overlay网络的连接限制：由于 Linux 内核的限制，当同一主机上同时存在 1000 个容器时，覆盖网络会变得不稳定，容器间的通信可能会中断。[Windows 容器与Linux 容器](https://oneuptime.com/blog/post/2026-02-08-how-to-switch-between-linux-and-windows-containers-on-docker-desktop/view)
##### 1.1.4.4 其他网络    
  - ipvlan网络：完全控制IPv4和IPv6寻址。
  - macvlan网络：为容器分配 MAC 地址，Docker守护程序通过容器的MAC地址将流量路由到容器。
  - none网络：将容器与主机和其他容器完全隔离。


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
  docker官方的学习资源分为入门、指南、手册、参考，先看入门，熟悉之后再看手册，参考reference用于重点查阅即可。
  - 菜鸟教程：
    - https://www.runoob.com/docker/docker-tutorial.html （快速入门）
    - https://dockerdocs.xuanyuan.me/tutorial（轩辕）
  
  - 官方教程（系统全面）：
    - 中文版：https://docs.docker.top/manuals/index.htm （分为入门、指南、手册、参考）
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
编写Dockfile文件，用docker build命令调用Dockfile文件，生成镜像。

[Dockerfile 概述-手册](https://docs.docker.top/build/concepts/dockerfile/index.htm)

[Docker build命令参考](https://docs.docker.top/reference/cli/docker/build-legacy/index.htm)

[Dockfile文件参考](https://docs.docker.top/reference/dockerfile/index.htm)

### 2.3 容器配置和创建（Docker compose yaml）
编写compose.yaml文件（文件中设置服务、容器名、卷和网络，引用镜像），用docker compose up -f ~/compose.yaml，生成容器。

[Docker compose手册](https://docs.docker.top/compose/index.htm)

[容器典型配置文档](https://docs.docker.top/engine/containers/start-containers-automatically/index.htm)

[Docker compose命令参考](https://docs.docker.top/reference/cli/docker/compose/index.htm)

[compose.yaml 文件参考](https://docs.docker.top/reference/compose-file/index.htm)

## 3 docker常用命令
[docker菜鸟常用命令教程](https://www.runoob.com/docker/docker-command-manual.html)

[docker官方中文版-全部命令](https://docs.docker.top/reference/cli/docker/index.htm)

[容器常用命令]()

[镜像常用命令]()

[存储常用命令]()

[网络常用命令]()

[Dockfile常用命令]()

[Docker Compose常用命令](https://docs.docker.top/reference/cli/docker/compose/index.htm)
