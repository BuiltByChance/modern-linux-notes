# 第 10 节　让 Ubuntu 虚拟桌面适应全屏

Workstation 已经切到全屏，Ubuntu 却仍挤在中央，四周留着黑边。要让客户机桌面跟着窗口调整分辨率，可以在 Ubuntu 内安装 VMware 的客户机工具，再切换全屏观察桌面边界。

## 在 Ubuntu Desktop 安装客户机工具

Ubuntu 20.04 和较新版本都适用发行版提供的 **open-vm-tools**。`open-vm-tools` 提供基础服务，`open-vm-tools-desktop` 补上图形桌面的集成功能。新装桌面虚拟机可直接在 **Ubuntu 终端** 运行以下命令，无需挂载工具光盘或更改虚拟光驱。[Broadcom 的 Ubuntu 安装说明](https://knowledge.broadcom.com/external/article/315313/installing-vmware-tools-in-an-ubuntu-vir.html) · [open-vm-tools 官方安装说明](https://github.com/vmware/open-vm-tools/wiki/FAQ)

```bash
sudo apt-get update
sudo apt-get install open-vm-tools open-vm-tools-desktop
```

第一条刷新软件包索引，第二条安装软件包。输入 `sudo` 密码时终端不显示字符，输完按回车即可。安装后保存工作，重启客户机并重新登录，做两项检查。

1. 在 Ubuntu 终端运行 `vmware-toolbox-cmd -v`，查看已安装的工具版本。[Broadcom 版本核对说明](https://knowledge.broadcom.com/external/article/344132/verifying-a-vmware-tools-build-version.html)
2. 拉大 Workstation 窗口或按 **Ctrl+Alt+Enter** 切换全屏。观察 Ubuntu 顶栏、桌面和 Dock 是否随窗口展开，原来的大块黑边是否消失。课中还从全屏工具栏的 **查看 → 独占模式** 隐藏了 Workstation 工具栏，按 **Ctrl+Alt** 可离开独占模式。

## 下载较慢时更换软件源

在课中的英文 Ubuntu 20.04 桌面打开 **Software & Updates → Ubuntu Software → Download from → Other…**。展开国家或地区，选一个适合自己网络的镜像，再点 **Choose Server**。讲师在 **China** 下选了 `mirrors.aliyun.com`，这是他当时的选择。[阿里云 Ubuntu 软件包镜像](https://mirrors.aliyun.com/ubuntu/)

用自己的账户密码授权，核对 **Download from** 已显示所选镜像，点 **Close → Reload** 刷新索引。**Revert** 会撤销修改。若还要安装系统更新，另开 **Software Updater → Install Now**。课中是在更新器提示后点 **Restart Now** 重启的。

## 看懂视频里的光盘和终端操作

课中用的是 Workstation 16 的 **虚拟机 → 重新安装 VMware Tools** 和光盘里的 **10.3.22**。这项菜单起初灰显，系统更新和重启后仍然如此。讲师关机，把 **CD/DVD (SATA)** 从 Ubuntu 安装 ISO 切到 **使用物理驱动器 → 自动检测**。开机提示宿主机没有对应的设备，随后 Tools 菜单可用，客户机能打开工具光盘。新装 Ubuntu 可用上面的 APT 路径，省去这段排查。[Broadcom 的客户机兼容表](https://knowledge.broadcom.com/external/article/313371/vmware-tools-compatibility-with-guest-op.html)

讲师在 Ubuntu 的文件管理器中把归档从光盘复制到桌面，再右击桌面空白处选 **Open in Terminal**。终端从 `~/Desktop` 打开，下面是视频中可以跟着读的命令。

```bash
ls
tar zxvf VMwareTools-10.3.22-15902021.tar.gz
cd vmware-tools-distrib/
ls
sudo ./vmware-install.pl
```

- `ls` 先核对文件名。`.tar.gz` 表示用 tar 把文件归档，再用 gzip 压缩。`tar zxvf` 中，`z` 处理 gzip，`x` 解包，`v` 显示解出的文件，`f` 表示后面跟归档文件名。键入文件名前几个字符后可按 **Tab** 补全。
- `cd` 进入解出的目录，第二次 `ls` 能看到 `vmware-install.pl`。`./` 指定当前目录中的脚本。脚本先推荐 open-vm-tools，并询问是否继续旧版安装，默认值为 `no`。讲师第一次按回车就返回了命令行，第二次重跑并输入 `yes`，之后接受默认路径和配置。
- 终端先后报告 **10.3.22 build-15902021** 安装和配置成功。后来手动弹出 `/dev/sr0` 时出现 **Unable to eject VMware Tools**。讲师随后用 `reboot` 重启并登录，Ubuntu 桌面仍能铺满屏幕。文件拖放和跨系统复制粘贴只出现在脚本提示里，本节验证的是显示效果。
