# 第 2 节　系统的认识 · 电脑开机后怎样进入操作系统

在记事本里敲一个字，键盘提供输入，操作系统把输入交给当前应用，记事本把文字显示出来。换成浏览器或聊天软件，完成的任务变了，应用仍然依赖操作系统管理设备、传递输入。

## 查看自己的 Windows 版本（02:03）

录课时，讲师右键桌面的“此电脑”，选择“属性”，在控制面板的“系统”页看到了 **Windows 10 专业版**。

现在可以打开 **设置 → 系统 → 关于**。在“Windows 规格”里读出自己安装的 Windows 版本和版本号，在“设备规格”的“系统类型”里查看是 32 位还是 64 位。[微软官方说明](https://support.microsoft.com/zh-cn/windows/experience/find-information-about-your-windows-device)

## 观察一台空白虚拟机开机（04:24–05:35）

宿主机是运行 VMware 的那台 Windows 电脑。下面观察的是 VMware 窗口里那台新建的虚拟机。

1. 在“新建虚拟机向导”的安装来源页，讲师选了 **稍后安装操作系统**。向导提示会创建一个空白硬盘，画面里的 ISO 文件栏呈灰色。这个选择让人能看到空盘开机的结果。
2. 讲师把客户机类型从“Linux / Ubuntu 64 位”切到“Microsoft Windows / Windows 10 x64”，固件页显示 **UEFI**。选择模板只是告诉 VMware 计划运行哪种系统。讲师暂停录制去完成创建，恢复时虚拟机已经建好。
3. 点击 **开启此虚拟机**。出现 VMware 标志后，查看画面左上角的启动信息，按设备逐行读。

| 屏幕提示 | 本次启动到了哪里 |
| --- | --- |
| 虚拟 NVMe 硬盘 … `No Media` | 固件未能从这块空白虚拟硬盘启动系统。 |
| 虚拟 SATA 光驱 … `No Media` | 光驱也没有提供可启动的安装介质。 |
| `EFI Network...` | 固件接着尝试网络启动。讲师在此处挂起虚拟机。随后打开“此电脑”的是原来的 Windows 宿主机。 |

**判断依据。** 本例能确定没装系统，是因为向导明确创建了空盘，安装镜像也没有挂载。若是原先能启动的电脑，同样的提示还可能意味着已有系统的引导信息无法读取。先看哪台机器、哪个设备提示了什么，再判断原因。[Broadcom 对启动设备回退的说明](https://knowledge.broadcom.com/external/article/419703/virtual-machine-fails-to-detect-boot-dev.html)

录课使用 VMware Workstation Pro 16。现在复现时可以从 Broadcom 登录下载 Workstation Pro，当前免费版本适用于个人、教育和商业用途，无需许可证密钥。[Workstation Pro 官方下载](https://support.broadcom.com/group/ecx/productdownloads?freeDownloads=true&subfamily=VMware+Workstation+Pro) · [下载与授权说明](https://knowledge.broadcom.com/external/article/368667/download-and-license-free-vmware-desktop.html)
