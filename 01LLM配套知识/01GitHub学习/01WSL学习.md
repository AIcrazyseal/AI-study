# WSL学习
> 2026.6.12

  在windows中安装WSL2（Windows Subsystem for Linux）和Ubuntu（Linux的一个版本），为容器Docker Desktop工具提供Linux运行环境。

  好处：轻量化、运行速度快，不用安装虚拟机，节省硬件资源；
  
## 1 Linux学习资源

  - Linux中文教程：https://www.runoob.com/linux/linux-tutorial.html（快速入门）

  - WSL2官方文档：https://learn.microsoft.com/zh-cn/windows/wsl/basic-commands（系统全面）

## 2 安装Linux
- 首先查看在线可安装的Linux版本： `wsl --list --online` 
- 然后安装指定的Linux版本：       `wsl --install <linux分发版>`
- 最后查看已安装的Linux版本：     `wsl --list --verbose`
- 卸载Linux分发版：              `wsl --unregister <linux分发版>`
完成以上三步，即成功安装WSL。
## 3 配置Linux
- 点击windows启动菜单>>WSL Settings，弹出的界面中可以对分配给Linux的CPU、硬盘、内存、网络等资源进行分配和调整；
- 可以在这个图形界面中点击“启动wsl.exe”，启动WSL命令行式对话框；
- 点击“欢迎使用WSL”，弹出WSL相关使用文档。
## 4 Linux常用命令
Linux命令大全详见：https://www.runoob.com/linux/linux-command-manual.html
### 4.1 安装命令
- 查看在线可安装的Linux版本： `wsl --list --online` 
- 安装指定的Linux版本：       `wsl --install <linux分发版>`
- 查看已安装的Linux版本：     `wsl --list --verbose`
- 启动指定的Linux版本：       `wsl --distribution <linux分发版>`
- 检查WSL状态：              `wsl --status`
- 设置默认 WSL 版本:         `wsl --set-default-version <linux版本：1/2>`
- 设置默认启动的WSL分发版：   `wsl --set-default <linux分发版>`
- 更新WSL:                  `wsl --update`
- 查询WSL命令用法：          `wsl --help`
- WSL关机：                 `wsl --shutdown`
- 装载Linux磁盘：            `wsl --mount <磁盘路径>`
- 卸载Linux磁盘：            `wsl --unmount <磁盘路径>`
- 卸载Linux分发版：          `wsl --unregister <linux分发版>`

### 4.2 文件/目录管理
- 更改文件所属用户与组：      `chown username:groupname filename`
- 更改文件权限：             `chmod [augo][rwx] filename`    
  - a:all; u:user; g:group; o:other
  - r:readable; w:writable; x:executable
- 文件绝对路径是从根目录（/）开始的完整路径；
- 文件相对路径
  - `.`：表示当前目录。
  - `..`：表示上一级目录（父目录）。
  - `~`：表示当前用户的家目录（例如/home/username）。
- 常用文件/目录管理命令
  - ls（list files）: 列出目录及文件名
  - cd（change directory）：切换目录
  - pwd（print work directory）：显示目前的目录
  - mkdir（make directory）：创建一个新的目录
  - rmdir（remove directory）：删除一个空的目录
  - cp（copy file）: 复制文件或目录
  - rm（remove）: 删除文件或目录
  - mv（move file）: 移动文件与目录，或修改文件与目录的名称  
  - cat（concatenate）：用于查看和连接文件

### 4.3 用户/用户组管理
- 用户账号管理
  - 添加用户账号：useradd 用户名
  - 删除用户帐号：userdel 用户名
  - 修改用户账号：usermod 用户名
- 用户密码管理：passwd [""/-l/u/d/f] 用户名  # 修改密码/-l:禁用账号/-u：口令解锁/-d：账号口令为空/-f：下次登录必须修改口令
- 用户组管理
  - 添加用户组：groupadd 选项 用户组名
  - 删除用户组：groupdel 用户组名
  - 修改用户组属性：groupmod [-g/o/n] 用户组   #-g：指定新的用户组标识号

### 4.4 磁盘管理

- df（disk free）：列出文件系统的整体磁盘使用量； `df [-ahikHTm] [目录或文件名]` # -h：以人类可读的方式显示输出结果（例如，使用 KB、MB、GB 等单位）。
- du（disk used）：检查磁盘空间使用量;           `du [-ahskm] 文件或目录名称`
- fdisk：用于磁盘分区：                         `fdisk [-l] 装置名称`
- 装载Linux磁盘：            `wsl --mount <磁盘路径>`
- 卸载Linux磁盘：            `wsl --unmount <磁盘路径>`
### 4.5 文件编辑
vi/vim是linux的文本编辑工具，使用方法详见：https://www.runoob.com/linux/linux-vim.html
### 4.6 apt命令
apt（Advanced Packaging Tool）是一个在 Debian 和 Ubuntu 中的 Shell **前端软件包管理器**。apt 命令提供了查找、安装、升级、删除某一个、一组甚至全部软件包的命令。apt 命令执行需要超级管理员权限(root)。
- apt 语法    `apt [options] [command] [package ...]`
  - options：可选，选项包括 -h（帮助），-y（当安装过程提示选择全部为"yes"），-q（不显示安装的过程）等等。
  - command：要进行的操作。
  - package：安装的包名。
## 5 官方学习资源
详见微软的https://learn.microsoft.com/zh-cn/windows/wsl/
