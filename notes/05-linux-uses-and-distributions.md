# 第 5 节　Linux 的用途与发行版家族

**内核决定系统怎样使用硬件，发行版决定你装到手的是哪套系统，桌面环境决定你怎样用窗口和菜单操作它。** 两个发行版都可以用 GNOME，同一个 Ubuntu 也能把启动栏从底部移到左侧。要确认机器上装的是哪个发行版，可在终端运行 `cat /etc/os-release`，查看 `PRETTY_NAME`。这是复习时可用的核对方法。[os-release 字段说明](https://www.freedesktop.org/software/systemd/man/latest/os-release.html)

## Linux 用在哪里

- **个人电脑**可以同时提供桌面和终端。桌面环境提供窗口、文件管理器等图形工具，终端里可以用 Bash、Vim 等程序完成工作。Linux 内核本身不包含整套桌面。它是独立实现的类 Unix 内核，内核整体按 GPL-2.0-only 授权，随发行版安装的软件各有许可证。[Linux 内核说明](https://docs.kernel.org/admin-guide/README.html) · [内核许可证](https://docs.kernel.org/process/license-rules.html)
- **服务器**通过网络向客户端提供服务。例如，用另一台手机登录同一账号，客户端可以向服务端查询同一份账户记录。机架式服务器是数据中心常见的硬件形态，普通电脑或虚拟机也可以运行服务。
- **超级计算机与嵌入式设备**都能使用 Linux。课中举的两端分别是 TOP500 榜上的计算系统，以及 Android 手机、部分路由器和电视等设备。读占比时要看榜单和日期，例如 2017 年 11 月 TOP500 的 500 台上榜系统均运行 Linux。[Linux 基金会对该期榜单的说明](https://www.linuxfoundation.org/blog/blog/linux-runs-all-of-the-worlds-fastest-supercomputers)

## 在终端里定位一段文字

1. 讲师在 Windows PowerShell 输入 `bash` 后进入 Linux 命令行。现在使用已安装的 WSL 时，可在 PowerShell 输入 `wsl` 进入默认发行版。已经在 Linux 终端里，可以直接从下一步开始。[微软 WSL 文档](https://learn.microsoft.com/zh-cn/windows/wsl/install)
2. 输入 `cd` 回到自己的主目录，`ls` 查看普通条目。讲师输入 `cls` 时，Bash 返回 `Command 'cls' not found`。在 Bash 里可用 `clear` 清屏。
3. 在装有 Vim 的环境输入 `vim .`，会打开当前目录的文件列表。将光标移到 `.bashrc`，按回车。只想直接查看这个文件，也可以从终端输入 `vim -R ~/.bashrc`。
4. 在 Vim 中按 `Esc`，输入 `:set nu` 并回车，左侧出现行号。输入 `:30` 并回车可跳到第 30 行。用 `/input` 加回车可查找下一个匹配。视频中选中的是第 30 行注释里的单词 `input`；不同机器的文件内容和行号会有差异。
5. 讲师演示到选中文字，随后取消选区。自己做完练习后，可按 `Esc`，输入 `:q!` 并回车，不保存地退出。

## 三组发行版怎么区分

发行版把内核、用户空间工具、软件仓库和默认配置组合起来。按上游项目归类，能帮助判断哪些软件包和使用经验可以迁移。课上选了以下三组，可从每组的项目主页继续查。

| 课上的分组 | 怎样理解这组里的名字 |
| --- | --- |
| Debian 系 | Ubuntu 和 Kali 都基于 Debian。两者各自选择软件、目标用户和默认配置。想练习桌面，可以从 Ubuntu Desktop 入手。[Debian 衍生发行版名录](https://www.debian.org/derivatives/) · [Debian 下载](https://www.debian.org/distrib/) · [Ubuntu Desktop 下载](https://ubuntu.com/download/desktop) |
| Fedora、CentOS 与红帽企业 Linux（RHEL） | 旧课里的 **CentOS Linux** 是按已发布的 RHEL 源码重新构建的发行版，7 和 8 都已结束维护。今天顺着开发方向看，是 Fedora Linux → CentOS Stream → RHEL；Stream 能预览下一次 RHEL 小版本的变化。选镜像时要看清 CentOS 的全名。[CentOS 项目说明](https://www.centos.org/cl-vs-cs/) · [Fedora Workstation 下载](https://fedoraproject.org/workstation/download/) · [CentOS Stream 下载](https://centos.org/download/) |
| openSUSE | 同一项目提供不同发行方式，例如 Leap 按版本发布，Tumbleweed 滚动更新，MicroOS 面向自动更新等场景。查镜像时先选适合自己用途的系列。[openSUSE 官方选择与下载入口](https://get.opensuse.org/) |

## 在 Ubuntu 上移动启动栏

Dock 是用来启动和切换应用的图标栏。讲师用的是已经运行的 **Ubuntu 20.04.1 LTS** 虚拟机，初始位置为底部。

1. 在桌面右上角的系统菜单打开 **Settings（设置）**。
2. 在这版 Ubuntu 打开 **Appearance（外观）→ Dock → Position on screen（屏幕位置）**，把 **Bottom（底部）** 改为 **Left（左侧）**。较新版 Ubuntu 在 **设置 → Ubuntu Desktop（Ubuntu 桌面）** 中调整 Dock。[Ubuntu 官方 Dock 设置说明](https://ubuntu.com/blog/kudos-for-kudu-customization)
3. 观察同一组应用图标。原先横排在底部的图标随即竖排到左边，就是更改已生效。左侧是讲师用来与 Debian 截图对照的位置，按自己的习惯选择即可。

## 课后比较练习

讲师建议用 1–3 天，从这三组中各选至少三个例子，在虚拟机体验后画一张关系图或写一份比较笔记。每个例子先记**发行版、版本和桌面环境**，再用同一个任务作比较，例如“在哪里改启动栏位置”。记下实际入口、成功后的变化、哪些操作可以照搬，以及一个值得保留或改进的地方。视频里的 Debian 10、Fedora 33 和 openSUSE 15.1 都是桌面截图，本节实际改动的是 Ubuntu 虚拟机的 Dock。
