# 第 6 节　VMware 虚拟机 · 选择练习环境与卸载旧版 Workstation

这门课选择在 Windows 里用 VMware Workstation Pro 运行 Linux。Windows 是**宿主系统**，装在虚拟机里的 Linux 是**客户系统**。Workstation 像普通应用一样从 Windows 启动，练习时不用在开机菜单里切换系统。

## 选择练习环境

| 方式 | 什么时候有用 |
| --- | --- |
| 实体机直接安装 | Linux 直接使用电脑硬件。先确认目标发行版支持这台机器的处理器和其他设备。 |
| 双系统 | Windows 和 Linux 分别安装在同一台电脑上，开机时选一个，切换通常要重启。 |
| 本地虚拟机 | 在现用系统里同时运行 Linux，适合跟课、开发和测试。选 Workstation 版本时先核对**宿主系统**的版本和位数，再核对想运行的 Linux。Workstation Pro 12 起要求 64 位宿主系统。[官方宿主系统兼容表](https://knowledge.broadcom.com/external/article/315653) |

讲师在 Windows 10 的 **控制面板 → 系统和安全 → 系统** 查看宿主机，页面显示专业版、64 位系统、32 GB 内存。这是物理电脑的信息。这节课还没给虚拟机分配内存。

如果团队已经提供 Linux 服务器、地址和账号，可以从自己的电脑远程登录。团队环境要升级时，先核对已有项目的兼容性和团队采用的版本。个人练习可以另选受支持的版本。

## 已装过 Workstation 时怎么处理

**首次安装可以直接跳到下载。** 讲师从 15.5 准备换到 16，担心覆盖安装时旧服务和驱动的处理，所以先手动卸载。Workstation 16 的官方升级说明也支持由新版安装程序移除旧版。自己升级时，先关闭运行中的虚拟机，再按目标版本的升级说明操作。[Workstation 16 升级说明](https://knowledge.broadcom.com/external/article/315594/vmware-workstation-16x-pro-sales-licensi.html) · [Workstation Pro 升级指南](https://knowledge.broadcom.com/external/article/343514/upgrading-vmware-workstation-pro.html)

**视频中手动卸载 15.5 的步骤**

1. 在 Windows 的已安装程序中找到 **VMware Workstation**。讲师用 Geek Uninstaller 搜索 `vmware`，双击结果，打开 VMware 自己的维护向导。Windows 也可从 **控制面板 → 程序 → 程序和功能 → VMware Workstation → 卸载/更改** 进入。[微软的程序卸载说明](https://support.microsoft.com/zh-cn/windows/apps/uninstall-or-remove-apps-and-programs-in-windows)
2. 点 **下一步**，在“更改、修复或删除安装”页选 **删除**。下一页询问要留下哪些资料，讲师保留了默认勾选的 **产品配置** 和 **产品许可证信息**。这两项分别决定是否留下旧版的配置和许可证记录。
3. 再点 **下一步 → 删除** 才开始执行。进度栏依次显示停止服务、卸载虚拟网络驱动程序等状态。
4. 看到向导显示**已完成**后点 **完成**。如果系统提示必须重启，**是**表示立即重启，**否**表示稍后手动重启。视频到这个提示为止，重启后的状态和新版安装留待后续。

## 现在从哪里下载

1. 用免费基础账号登录 Broadcom Support Portal。在 **My Downloads → Free Software Downloads** 搜索 **VMware Workstation Pro**，选择 **for Windows** 和适合宿主系统的发行版本。[Workstation Pro 官方下载](https://support.broadcom.com/group/ecx/productdownloads?subfamily=VMware%20Workstation%20Pro&freeDownloads=true)
2. 打开 **Terms and Conditions** 阅读条款，返回勾选同意后下载。如首次下载提示补全资料，按页面提示完成。免费入口可用普通基础账号访问。[Broadcom 下载步骤](https://knowledge.broadcom.com/external/article/397417/downloading-free-software-from-the-broad.html)

视频里的 15.5 和 16 是录制时的版本。官方后来改用年份和半年度命名，例如 **26H1**。Broadcom 的免费政策适用于 **Workstation Pro 17.5.2 及以上**，覆盖个人、教育和商业用途，免费版无需输入许可证密钥。[官方版本公告](https://blogs.vmware.com/cloud-foundation/2026/05/14/announcing-vmware-workstation-and-fusion-26H1/) · [Broadcom 授权说明](https://knowledge.broadcom.com/external/article/368667/download-and-license-vmware-desktop-hyper.html)
