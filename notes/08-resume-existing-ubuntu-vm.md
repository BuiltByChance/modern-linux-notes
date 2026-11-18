# 第 8 节　升级 Workstation 后继续使用原有的 Ubuntu 虚拟机

Workstation 的程序和虚拟机文件分开保存。从 15 换到 16 后，先查看原机器是否还在库中。课里的 Ubuntu 20.04 保留了配置、虚拟磁盘和挂起状态，讲师直接恢复到了原桌面，虚拟硬件仍保持 15.x 兼容级别。[Workstation 16 官方升级说明](https://knowledge.broadcom.com/external/article/315594)

## 找到旧机器并恢复

1. 打开 Workstation。要确认宿主机上安装的软件版本，查看 **帮助 → 关于 VMware Workstation**。视频中显示 **16.1.0，构建号 17198959**。
2. 在左侧**库 → 我的计算机**中选择旧虚拟机，看详情里的**状态、配置文件、硬件兼容性**。课里的机器名为 `Ubuntu642004`，状态为**已挂起**，配置文件是讲师电脑上的 `E:\VmSystem\ubuntu2004\Ubuntu642004.vmx`，兼容性显示 **Workstation 15.x 虚拟机**。库中没看到条目时，可以用 **文件 → 打开** 选择原来的 `.vmx` 配置文件。它引用的 `.vmdk` 虚拟磁盘也要保留，磁盘可能放在另一块盘上。[查找虚拟机配置及磁盘位置](https://knowledge.broadcom.com/external/article/308646/locating-a-hosted-virtual-machines-files.html)
3. 对状态为**已挂起**的机器，点 **继续运行此虚拟机**。此时详情页上的灰色桌面只是预览。等“正在还原虚拟机状态”进度结束、控制台显示原来的 Ubuntu 桌面，才算恢复了这次会话。讲师没有更改硬件兼容性，也没有重装 Ubuntu。

## VMware Tools 是否需要重装

讲师在 **虚拟机 → 重新安装 VMware Tools…** 上停留后关闭了菜单，未执行安装。要确认 Ubuntu 中的工具包，可在客户机终端运行 `dpkg -l open-vm-tools open-vm-tools-desktop`，行首的 `ii` 表示相应软件包已安装。Broadcom 推荐 Ubuntu 14.x 及以上使用发行版提供的 `open-vm-tools`，图形桌面的集成功能由 `open-vm-tools-desktop` 补充。[Broadcom 的 Ubuntu 工具说明](https://knowledge.broadcom.com/external/article/315313) · [open-vm-tools 项目 FAQ](https://github.com/vmware/open-vm-tools/wiki/FAQ)

判断客户机兼容性要看具体小版本。**Workstation Pro 15.5.5** 的官方发行说明已经将 **Ubuntu 20.04** 列入新增支持的客户机系统。本节验证的是 16.1.0 能恢复讲师这台旧虚拟机。[VMware 15.5.5 发行说明存档](https://web.archive.org/web/20200615134900id_/https://docs.vmware.com/en/VMware-Workstation-Pro/15.5/rn/VMware-Workstation-1555-Pro-Release-Notes.html)

## 验证后保留或删除

- **以后还要用这台机器**，在 Workstation 工具栏的电源下拉菜单选 **关闭客户机**，在确认框点 **关机**。等详情页显示**已关机**即可，配置和磁盘都留在原处。
- **只想整理库列表**，对条目使用**从库中移除**，磁盘上的文件仍可用原 `.vmx` 再次打开。
- **确定整台虚拟机都不要了**，先关机并备份要保留的数据，再选中目标机，通过 **虚拟机 → 管理 → 从磁盘中删除** 操作。这会删除保存在虚拟机里的数据。[Broadcom 删除说明](https://knowledge.broadcom.com/external/article/315656)

片尾讲师为了下节从零安装，在 Windows 资源管理器中永久删除了自己 E 盘和 O 盘上的两个目录。E 盘目录属性显示约 645 KB、共 7 个文件，里面可见配置文件和日志。O 盘目录的内容没有展开。要继续使用原机器，做到确认恢复或关机即可。
