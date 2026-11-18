# 第 9 节　在 VMware 虚拟机中安装 Ubuntu Desktop

Ubuntu 的 `.iso` 充当安装光盘，Workstation 新建的虚拟磁盘（`.vmdk`）充当客户机硬盘。先从 ISO 启动，把系统写入虚拟硬盘，再从虚拟硬盘重启，用刚创建的账户登录。

## 选对安装镜像

要得到课中的图形桌面，选 **Ubuntu Desktop**。Server 镜像用于服务器安装，默认不带这套桌面。普通 Intel 或 AMD 64 位电脑跟做时选 **AMD64**。可以直接下载 ISO，也可以用 BitTorrent 下载，最后挂载的是 `.iso` 文件。[Ubuntu Desktop 下载](https://ubuntu.com/download/desktop) · [其他下载方式](https://ubuntu.com/download/alternative-downloads)

| 练习目标 | 镜像与资源 |
| --- | --- |
| 对照视频里的安装器 | 讲师使用 `ubuntu-20.04.1-desktop-amd64.iso`。官方仍保留这个文件，同一系列也有 20.04.6。20.04 LTS 的标准安全维护已于 2025 年 5 月结束。[20.04.1 官方存档](https://old-releases.ubuntu.com/releases/20.04.1/) · [20.04.6 镜像](https://releases.ubuntu.com/20.04/) · [维护周期](https://ubuntu.com/about/release-cycle) |
| 安装当前桌面 LTS | 截至 2026-11-18，官方下载页提供 **26.04.1 LTS**，列出的配置是 2 GHz 双核处理器、6 GB 内存和 25 GB 可用磁盘空间。给虚拟机分配磁盘时要留足空间，视频示例的 20 GB 低于这一要求。VMware 将 Ubuntu 26.04 列为 Workstation 26H1 新增支持的客户机。[Ubuntu 官方下载与配置](https://ubuntu.com/download/desktop) · [VMware 客户机支持说明](https://blogs.vmware.com/cloud-foundation/2026/05/14/announcing-vmware-workstation-and-fusion-26H1/) |

## 新建虚拟机并挂载 ISO

在 Workstation 选择 **文件 → 新建虚拟机 → 自定义（高级）**。按下面的顺序填写，数值和盘符均为讲师电脑上的示例。

| 向导页面 | 视频中的选择与作用 |
| --- | --- |
| 兼容性与客户机 | 保留 **Workstation 16.x**，选 **稍后安装操作系统**，再选 **Linux → Ubuntu 64 位**。这样能手动挂载 ISO 并逐页操作 Ubuntu 安装器。 |
| 名称与位置 | 名称为 `ubuntu2004x64`，目录为 `O:\VmSystem\ubuntu2004x64`。自己选有足够空间的目录，用版本和架构命名，方便与其他虚拟机区分。 |
| 处理器与内存 | 讲师的宿主机有 16 个逻辑处理器、32 GB 内存，最终给客户机 **2 个处理器 × 每个 2 核，共 4 个 vCPU**，内存 **8192 MB**。分配时还要给 Windows 和正在运行的程序留资源。 |
| 网络与磁盘 | 保留 **NAT → LSI Logic → SCSI**，选 **创建新虚拟磁盘**。NAT 让客户机通过宿主机的网络连接访问外部网络。旧版示例磁盘容量为 **20 GB**，文件名为 `ubuntu2004x64.vmdk`。 |
| 磁盘空间分配 | 勾选 **立即分配所有磁盘空间**，并选 **将虚拟磁盘存储为单个文件**。预分配会在创建时占用设定的容量。宿主机空间紧张时，可以取消预分配，让磁盘文件随写入增长。单文件或拆分文件是另一个独立选项。 |
| 安装光盘及设备 | 在最后的摘要页点 **自定义硬件 → 新 CD/DVD（SATA）→ 使用 ISO 映像文件 → 浏览**，选中下载好的 ISO，保留 **启动时连接**。课中移除了用不到的打印机，保留了 USB 控制器、声卡和显示器。 |

关闭硬件设置，点 **完成**，等虚拟磁盘创建好，再点 **开启此虚拟机**。出现 Ubuntu 安装器的 **Try Ubuntu / Install Ubuntu** 欢迎页，说明已从 ISO 启动。

## 在客户机内安装 Ubuntu 20.04

1. 选择界面语言，点 **Install Ubuntu**，再确认键盘布局。讲师用 **English** 和 **English (US)**，便于按课程里的英文界面和目录名操作。自己选熟悉的语言和实际键盘布局即可。
2. 在 **Updates and other software** 选 **Minimal installation**，得到浏览器和基本工具。想预装办公、游戏和媒体应用可选 **Normal installation**。课里“安装时下载更新”灰显，第三方驱动和媒体格式选项留空。遇到相同界面，可在 **虚拟机 → 设置 → 网络适配器** 核对网络模式和连接状态。课中显示 NAT、“已连接”和“启动时连接”，之后安装日志也出现了取包进度。26.04 的交互式安装改用 **Default selection / Extended selection** 区分基本应用和扩展应用。[新版 Ubuntu 安装指南](https://ubuntu.com/desktop/docs/en/26.04/tutorial/install-ubuntu-desktop/)
3. 在 **Installation type** 选 **Erase disk and install Ubuntu → Install Now**。这一步会清空所选磁盘，课里的目标是刚建的空白虚拟盘 `sda`。在 **Write the changes to disks?** 核对目标后点 **Continue**，让安装器自动分区。视频中列出第 1 和第 5 分区，第 5 分区格式为 ext4，无须照抄分区编号。
4. 选择时区，创建本地账户并设置自己的密码。讲师选 **Shanghai**，示例用户名为 `frank`，保留 **Require my password to log in**。记住用户名和密码，重启后要用它们登录。
5. 安装中可点进度文字旁的小箭头展开日志。先看当前动作，再结合时间和后续记录判断是否仍在推进，例如取包、安装语言包、配置硬件。视频末尾点 **Skip** 跳过当时的软件包下载，随后才出现 **Installation Complete**。
6. 点 **Restart Now**。若提示移除安装介质，确认虚拟光驱不再从安装 ISO 引导，再按 **Enter**。用刚创建的账户登录，完成首次使用向导，看到 Dock、主目录和废纸篓，即已进入安装好的桌面。要核对版本，可在客户机终端运行 `grep PRETTY_NAME /etc/os-release`。
