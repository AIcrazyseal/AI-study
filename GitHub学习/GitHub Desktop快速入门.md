# GitHub Desktop 使用入门 
## **自我总结**  **2026.2.2**

了解如何设置、验证和配置 GitHub Desktop，以便直接从您的计算机直接参与项目。

## 一、快速入门简介

GitHub Desktop 是免费的开放源代码应用程序，可帮助处理托管在 GitHub 或其他 Git 托管服务上的代码。 使用 GitHub Desktop，可以在图形用户界面中执行提交和推送更改等 Git 命令，而不是使用命令行。 有关详细信息，请参阅“[关于 GitHub Desktop](/zh/desktop/installing-and-configuring-github-desktop/overview/about-github-desktop)”。

本指南将介绍设置应用程序、验证帐户、配置基本设置，以及介绍使用 GitHub Desktop 管理项目的基础知识，帮助您开始使用 GitHub Desktop。 在读完本指南后，您将能够使用 GitHub Desktop 协作处理项目并连接到远程仓库。

您可能会发现，在开始使用 GitHub 之前，基本了解 Git 和 GitHub Desktop 会有帮助。 有关详细信息，请参阅以下文章。

* [使用 Git](/zh/get-started/using-git)
* [了解 GitHub](/zh/get-started/learning-about-github)
* [GitHub 入门文档](/zh/get-started)

GitHub Desktop 是一个开源项目。 您可以查看路线图、为项目做出贡献，或者打开议题以提供反馈或功能请求。 有关详细信息，请参阅 [`desktop/desktop`](https://github.com/desktop/desktop) 存储库。

## 第 1 部分：安装和身份验证

您可以在任何支持的操作系统上安装 GitHub Desktop。 有关详细信息，请参阅“[GitHub Desktop 支持的操作系统](/zh/desktop/overview/supported-operating-systems-for-github-desktop)”。

要安装 GitHub Desktop，请访问 [GitHub Desktop](https://desktop.github.com/) 的下载页面。 有关详细信息，请参阅“[安装 GitHub Desktop](/zh/desktop/installing-and-authenticating-to-github-desktop/installing-github-desktop)”。

在安装 GitHub Desktop 后，您可以使用您在 GitHub 或 GitHub Enterprise 上的帐户验证应用程序。 身份验证允许您连接到 GitHub 或 GitHub Enterprise 上的远程仓库。

<div class="ghd-tool mac">

1. 在向 GitHub 或 GitHub Enterprise 进行身份验证之前，你需要一个帐户。有关详细信息，请参阅 [在 GitHub 上创建帐户](/zh/get-started/start-your-journey/creating-an-account-on-github)。
2. 在菜单栏中，选择“GitHub Desktop”，然后单击“设置”。\
   <img src="https://docs.github.com/assets/cb-10737/mw-1440/images/help/desktop/windows-choose-options.webp" width=60% style=“display:block;margin:0”>
   
3. 在“设置”窗口中的“帐户”窗格中，单击相应的“登录”按钮。\ 使用“登录到 GitHub Enterprise”登录到 GitHub Enterprise Server 或 具有数据驻留的 GitHub Enterprise Cloud。\

   ![“设置”窗口中“帐户”窗格的屏幕截图。 会显示标记为“登录到 GitHub.com”和“登录到 GitHub Enterprise”的蓝色按钮。](/assets/images/help/desktop/sign-in-github.png)
4. 按照以下步骤登录。 有关身份验证的详细信息，请参阅“[在 GitHub Desktop 中向 GitHub 进行身份验证](/zh/desktop/installing-and-authenticating-to-github-desktop/authenticating-to-github-in-github-desktop)”。

</div>

<div class="ghd-tool windows">

1. 在向 GitHub 或 GitHub Enterprise 进行身份验证之前，你需要一个帐户。有关详细信息，请参阅 [在 GitHub 上创建帐户](/zh/get-started/start-your-journey/creating-an-account-on-github)。
2. 使用文件”菜单，然后单击“选项” 。

   ![Windows 上的“GitHub Desktop”菜单栏的屏幕截图。 在展开的“文件”下拉菜单中，以橙色框出了“选项”项。](/assets/images/help/desktop/windows-choose-options.png)
3. 在“选项”窗口中的“帐户”窗格中，单击相应的“登录”按钮\*\*\*\*。 使用“登录到 GitHub Enterprise”登录到 GitHub Enterprise Server 或 具有数据驻留的 GitHub Enterprise Cloud\*\*\*\*。

   ![“选项”窗口中“帐户”窗格的屏幕截图。 会显示标记为“登录到 GitHub.com”和“登录到 GitHub Enterprise”的蓝色按钮。](/assets/images/help/desktop/windows-sign-in-github.png)
4. 按照以下步骤登录。 有关身份验证的详细信息，请参阅“[在 GitHub Desktop 中向 GitHub 进行身份验证](/zh/desktop/installing-and-authenticating-to-github-desktop/authenticating-to-github-in-github-desktop)”。

</div>

## 第 2 部分：配置和自定义 GitHub Desktop

安装 GitHub Desktop 后，您可以配置并自定义应用程序，使之最适合您的需求。

<div class="ghd-tool mac">

你可以连接或删除 GitHub 或 GitHub Enterprise 上的帐户、选择默认文本编辑器或 shell、编辑 Git 配置、更改 GitHub Desktop 的外观、自定义系统对话框，以及在 GitHub Desktop Settings 窗口中设置隐私首选项。 有关详细信息，请参阅“[在 GitHub Desktop 中配置基本设置](/zh/desktop/configuring-and-customizing-github-desktop/configuring-basic-settings-in-github-desktop)”。

![“设置”窗口的屏幕截图。 左侧边栏中的第一个选项处于选中状态并显示为蓝色。](/assets/images/help/desktop/sign-in-github.png)

</div>

<div class="ghd-tool windows">

您可以连接或删除 GitHub 或 GitHub Enterprise 上的帐户、选择默认文本编辑器或 shell、编辑 Git 配置、更改 GitHub Desktop 的外观、自定义系统对话框，以及在 GitHub Desktop Options（选项）窗口中设置隐私首选项。 有关详细信息，请参阅“[在 GitHub Desktop 中配置基本设置](/zh/desktop/configuring-and-customizing-github-desktop/configuring-basic-settings-in-github-desktop)”。

![“选项”窗口的屏幕截图。 左侧边栏中的第一个选项处于选中状态并显示为蓝色。](/assets/images/help/desktop/windows-sign-in-github.png)

</div>

## 第 3 部分：通过 GitHub Desktop 参与项目

在安装、验证和配置应用程序后，便可开始使用 GitHub Desktop。 您可以创建、添加或克隆仓库，并使用 GitHub Desktop 来管理对您的仓库的参与。

### 创建、添加和克隆仓库

可以在“GitHub Desktop”菜单栏中选择“File”，然后单击“New repository...”来创建新的仓库。\*\*\*\*\*\*\*\* 有关详细信息，请参阅“[使用 GitHub Desktop 创建第一个仓库](/zh/desktop/overview/creating-your-first-repository-using-github-desktop)”。

可以通过选择“File”，然后单击“Add Local Repository...”，从本地计算机添加仓库。\*\*\*\*\*\*\*\* 有关详细信息，请参阅“[将仓库从本地计算机添加到 GitHub Desktop](/zh/desktop/adding-and-cloning-repositories/adding-a-repository-from-your-local-computer-to-github-desktop)”。

可以通过选择“File”，然后单击“Clone Repository...”，从 GitHub 克隆仓库。\*\*\*\*\*\*\*\* 有关详细信息，请参阅“[从 GitHub Desktop 克隆和复刻仓库](/zh/desktop/adding-and-cloning-repositories/cloning-and-forking-repositories-from-github-desktop)”。

<div class="ghd-tool mac">

![Mac 上的菜单栏的屏幕截图。 存储库的操作在打开的“文件”下拉菜单中列出。](/assets/images/help/desktop/mac-file-menu.png)

</div>

<div class="ghd-tool windows">

![Windows 上的“GitHub Desktop”菜单栏的屏幕截图。 存储库的操作在打开的“文件”下拉菜单中列出。](/assets/images/help/desktop/windows-file-menu.png)

</div>

### 在分支中更改

您可以使用 GitHub Desktop 创建项目分支。 分支将开发工作与仓库中的其他分支相分隔，以便您安全地尝试更改。 有关详细信息，请参阅“[在 GitHub Desktop 中管理分支](/zh/desktop/making-changes-in-a-branch/managing-branches-in-github-desktop)”。

对分支进行更改后，您可以在 GitHub Desktop 中审查它们，并创建提交以跟踪您的更改。 有关详细信息，请参阅“[在 GitHub Desktop 中提交并审查对项目的更改](/zh/desktop/making-changes-in-a-branch/committing-and-reviewing-changes-to-your-project-in-github-desktop)”。

如果要远程访问更改或与他人共享更改，您可以将提交推送到 GitHub。 有关详细信息，请参阅“[将更改从 GitHub Desktop 推送到 GitHub](/zh/desktop/making-changes-in-a-branch/pushing-changes-to-github-from-github-desktop)”。

### 使用 GitHub Desktop 进行协作

您可以使用 GitHub Desktop 创建议题或拉取请求来与其他人协作处理项目。 议题有助于您跟踪想法和讨论项目可能发生的变化。 拉取请求可让您与他人共享提议的更改、接收反馈并将更改合并到项目中。 有关详细信息，请参阅“[从 GitHub Desktop 创建问题或拉取请求](/zh/desktop/working-with-your-remote-repository-on-github-or-github-enterprise/creating-an-issue-or-pull-request-from-github-desktop)”。

您可以在 GitHub Desktop 中查看您自己或您的协作者的拉取请求。 在 GitHub Desktop 中查看拉取请求可让您查看任何提议的更改，以及在默认文本编辑器中打开项目文件和仓库进行其他更改。 有关详细信息，请参阅“[在 GitHub Desktop 中查看拉取请求](/zh/desktop/working-with-your-remote-repository-on-github-or-github-enterprise/viewing-a-pull-request-in-github-desktop)”。

### 保持本地仓库同步

当您对更改本地仓库或者其他人更改远程仓库时，您需要将项目的本地副本与远程仓库同步。 GitHub Desktop 可以通过推送和拉取提交来保持项目本地副本与远程版本同步。 有关详细信息，请参阅“[在 GitHub Desktop 中同步分支](/zh/desktop/working-with-your-remote-repository-on-github-or-github-enterprise/syncing-your-branch-in-github-desktop)”。
