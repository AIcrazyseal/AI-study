## WSL学习
> 2026.6.12

  在windows中安装WSL2（Windows Subsystem for Linux）和Ubuntu（Linux的一个版本），为容器Docker Desktop工具提供Linux运行环境。

  好处：轻量化、运行速度快，不用安装虚拟机，节省硬件资源；
  
### 1 Linux学习资源

  - Linux中文教程：https://www.runoob.com/linux/linux-tutorial.html（快速入门）

  - WSL2官方文档：https://learn.microsoft.com/zh-cn/windows/wsl/basic-commands（系统全面）

### 2 安装Linux
- 首先查看在线可安装的Linux版本： `wsl --list --online` 
- 然后安装指定的Linux版本：       `wsl --install <linux分发版>`
- 最后查看已安装的Linux版本：     `wsl --list --verbose`
完成以上三步，即成功安装WSL。
### 3 配置Linux
- 点击windows启动菜单>>WSL Settings，弹出的界面中可以对分配给Linux的CPU、硬盘、内存、网络等资源进行分配和调整；
- 可以在这个图形界面中点击“启动wsl.exe”，启动WSL命令行式对话框；
- 点击“欢迎使用WSL”，弹出WSL相关使用文档。
### 4 Linux常用命令
- 查看在线可安装的Linux版本： `wsl --list --online` 
- 安装指定的Linux版本：       `wsl --install <linux分发版>`
- 查看已安装的Linux版本：     `wsl --list --verbose`
- 检查WSL状态：              `wsl --status`
- 设置默认 WSL 版本:         `wsl --set-default-version <linux版本：1/2>`
- 设置默认启动的WSL分发版：   `wsl --set-default <linux分发版>`
- 更新WSL:                  `wsl --update`
- 查询WSL命令用法：          `wsl --help`
- WSL关机：                 `wsl --shutdown`
- 装载Linux磁盘：            `wsl --mount <磁盘路径>`
- 卸载Linux磁盘：            `wsl --unmount <磁盘路径>`

### 5 官方学习资源
详见微软的https://learn.microsoft.com/zh-cn/windows/wsl/
