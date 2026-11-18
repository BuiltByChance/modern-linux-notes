# 第 7 节　在 Windows 安装 VMware Workstation Pro

本节把 Workstation 安装在 Windows 宿主机上。讲师使用的是 **Workstation Pro 16.1.0（构建号 17198959）**。安装这一步完成后，才有了创建 Linux 虚拟机的工具。

## 取得安装包

用免费基础账号登录 Broadcom Support Portal，在 **My Downloads → Free Software Downloads → VMware Workstation Pro** 选择 Windows 版本。打开并阅读 **Terms and Conditions**，返回勾选同意后下载。官方现已采用按年份和半年度命名的版本号，例如 26H1。[Workstation Pro 官方下载](https://support.broadcom.com/group/ecx/productdownloads?subfamily=VMware%20Workstation%20Pro&freeDownloads=true) · [下载步骤](https://knowledge.broadcom.com/external/article/397417/downloading-free-software-from-the-broad.html) · [版本公告](https://blogs.vmware.com/cloud-foundation/2026/05/14/announcing-vmware-workstation-and-fusion-26H1/)

## 运行 Windows 安装向导

1. 使用有本机管理员权限的账号运行下载的 `.exe`，按向导阅读并接受许可协议。课中直接双击桌面上已有的安装包。[官方 Windows 安装说明](https://knowledge.broadcom.com/external/article/387947/installing-vmware-workstation-pro.html)
2. 在**自定义安装**页确认程序的位置。保留默认目录即可，也可点**更改**。讲师用的是 `E:\DevTools\VMware\`，这个路径存放 Workstation 程序。在他的机器上，该目录还留有已卸载的 15 版程序文件，所以他先清理了旧文件。首次安装可直接选目录继续。已有虚拟机的用户要区分程序目录与存放 `.vmx`、`.vmdk` 的虚拟机目录。
3. 按自己的用途选择以下选项，再点**下一步 → 安装**。

| 向导选项 | 视频中的选择 | 怎样取舍 |
| --- | --- | --- |
| 增强型键盘驱动程序 | 手动勾选。16.1 的向导提示启用它需要重启。 | 旧版用它改善对国际键盘布局和额外按键的处理。Windows 版从 **17.6** 起已移除此驱动，新版可直接继续。[VMware 官方手册](https://techdocs2-prod.adobecqms.net/content/dam/broadcom/techdocs/us/en/pdf/vmware/desktop-hypervisors/workstation/vmware-workstation-pro-17-0.pdf#page=32) |
| 将控制台工具添加到系统 PATH | 保留勾选 | 方便从任意目录打开终端后按名称调用工具。用开始菜单打开图形界面不依赖此项。 |
| 启动时检查产品更新、加入客户体验提升计划（CEIP） | 两项都取消 | 前者控制启动时是否检查新版，后者决定是否向 VMware 提交产品使用信息，可以分别选择。 |
| 创建快捷方式 | 只选**开始菜单程序文件夹**，取消**桌面** | 决定以后从哪里启动程序。按课中选择安装，桌面上没有快捷方式也属正常。 |

## 完成安装并核对结果

看到**安装向导已完成**后，当前免费版可选**完成**。Broadcom 的免费政策覆盖 **Workstation Pro 17.5.2 及以上**，适用于个人、教育和商业用途，无需输入许可证密钥。[Broadcom 下载与授权说明](https://knowledge.broadcom.com/external/article/368667/download-and-license-vmware-desktop-hyper.html)

如果向导提示需要重启，保存手头的工作并重启 **Windows 宿主机**。随后从开始菜单打开 **VMware Workstation Pro**，在 **帮助 → 关于（Help → About）** 中核对版本和构建号。视频展示到安装完成并弹出重启提示，启动后的版本核对是跟做时可以补上的一步。[官方版本核对方法](https://knowledge.broadcom.com/external/article/320235)
