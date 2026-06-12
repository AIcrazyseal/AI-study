# docker desktop学习
> 2026.6.12

## 1 Docker学习资源
  
  菜鸟教程：https://www.runoob.com/docker/docker-tutorial.html（快速入门）
           https://dockerdocs.xuanyuan.me/tutorial（轩辕）
  
  官方中文教程：https://docs.docker.top/get-started/index.htm（系统全面）

  官方英文教程：https://docs.docker.com/get-started/get-docker/（系统全面）

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
