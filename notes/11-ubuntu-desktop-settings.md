# 第 11 节　Ubuntu 桌面设置

课中使用英文界面的 Ubuntu Desktop 20.04.1 LTS。从桌面右上角的系统菜单打开 **Settings**，也可以在活动概览中搜索设置名称。

## 外观、显示和键盘

| 想做的事 | Ubuntu 20.04 的入口和检查方法 |
| --- | --- |
| 换壁纸 | 在 **Background** 点选缩略图，背景会立即改变。带时钟标志的选项会轮换图片；想固定一张图，就选单张壁纸。讲师最后选了树林照片。 |
| 改主题和 Dock | 在 **Appearance → Window colors** 选择 Light、Standard 或 Dark。在同页的 **Dock** 区域调整自动隐藏、图标大小和屏幕位置。讲师最后用 **Dark**，Dock 在 **Bottom**，图标大小为 **48**，自动隐藏关闭。这些都是个人偏好，可以直接观察桌面比较效果。 |
| 调整画面大小 | **Displays → Resolution** 设置像素数量，**Scale** 调整文字和界面元素的大小。讲师的虚拟机显示 **1920 × 1080、100%**；演示中展开了分辨率列表，也指出了 200% 选项。 |
| 更改鼠标习惯 | **Mouse & Touchpad** 可选择左右主键、调整指针速度，或用 **Natural Scrolling** 改变滚动方向。 |
| 打开终端 | 在 **Keyboard Shortcuts → Launchers → Launch terminal** 查看本机绑定。课中显示 **Ctrl+Alt+T**，按下后出现终端和 Shell 提示符。 |

## 分清熄屏、锁屏和挂起

在 **Settings → Privacy → Screen Lock**，讲师把 **Blank Screen Delay** 从 **5 minutes** 改为 **Never**，让讲课时屏幕保持点亮。稍后打开 **Power**，其中 **Blank Screen** 也显示 **Never**。

| 选项 | 控制的行为 | 讲师虚拟机上的值 |
| --- | --- | --- |
| Blank Screen Delay | 空闲多久后关闭屏幕显示 | Never |
| Automatic Screen Lock / Automatic Screen Lock Delay | 熄屏后是否锁定会话，以及等待多久才锁定 | 开启，延迟为 Screen Turns Off（熄屏时） |
| Lock Screen on Suspend | 系统挂起时是否锁定会话 | 开启 |
| Automatic Suspend（Power 页） | 系统是否在空闲后自动挂起 | Off |

新版 Ubuntu 可在 **设置 → 电源** 查熄屏时间，在 **设置 → 隐私与安全 → 屏幕锁定** 查自动锁屏。要让屏幕常亮时，先核对电源选项即可。[GNOME 熄屏设置](https://help.gnome.org/gnome-help/display-blank.html.zh_CN) · [GNOME 自动锁屏设置](https://help.gnome.org/gnome-help/session-screenlocks.html.zh_CN)

## 区域格式、时钟与系统信息

- **Region & Language** 把界面语言（Language）、日期和计量格式（Formats）、输入源（Input Sources）分开设置。讲师保留美式英语界面和美式键盘，在 **Formats** 把“中国”改为 **United States**。可先看右侧的日期、数字、纸张预览，再点 **Done**。页面随后提示重新启动会话；保存工作后退出并重新登录即可生效。新版入口为 **设置 → 系统 → 区域与语言**。[GNOME 区域格式说明](https://help.gnome.org/gnome-help/session-formats.html.zh_CN)
- **Date & Time → Time Format** 可在 **AM/PM** 和 **24-hour** 之间切换，顶栏时钟会即时变化。自动校时、时区和显示格式各自独立。课中已启用自动校时，时区为上海，最后保留 24 小时制。
- **Users** 可查当前登录账户，需要改受保护的设置时点 **Unlock**。**Default Applications → Web** 可查哪个浏览器会打开链接。讲师的 Ubuntu 显示 Firefox。
- **About** 可核对客户机实际识别的硬件和系统。示例显示 **7.7 GiB 内存、4 个虚拟 CPU、21.5 GB 磁盘总容量**，系统为 **Ubuntu 20.04.1 LTS、64 位、GNOME 3.36.3、X11**，虚拟化平台为 **VMware**。

## 找已装应用和可安装软件

20.04 的 Dock 网格按钮 **Show Applications → All** 可以找已装应用。讲师从这里打开 **Characters** 浏览符号和表情；同页也能找到 **Screenshot**。要找新软件则打开 **Ubuntu Software**，其中 **Explore** 浏览可安装应用，**Installed** 列出已安装项目，**Updates** 列出待更新项目。

课中商店首页和 `vimix` 的详情页能打开，但多个分类只有占位符，搜索 `spotify` 也一直在加载。更新页列出 5 项。视频结束前没有安装或更新软件，也没有确认加载异常的原因。

Ubuntu 从 23.10 起用 **App Center（应用中心）** 取代 Ubuntu Software。在新版桌面从 Dock 打开 App Center，搜索应用并进入详情，核对后点 **Install**。若要找课里没搜到的 Spotify，厂商也提供 Linux 安装入口。[Ubuntu 商店更名说明](https://ubuntu.com/blog/ubuntu-desktop-23-10-mantic-minotaur-deep-dive) · [Ubuntu 26.04 安装应用指南](https://ubuntu.com/desktop/docs/en/26.04/how-to/software/install-an-application/) · [Spotify 官方 Linux 下载页](https://www.spotify.com/download/linux/)

课中另开的 **Additional Drivers** 属于 **Software & Updates**。它列出了讲师虚拟机的 VMware SVGA II 虚拟显卡，讲师查看后就关闭了窗口。Ubuntu 26.04 默认不预装这套设置工具，需要同一图形界面时可用 `sudo apt install software-properties-gtk` 安装。[Ubuntu 26.04 发行说明](https://documentation.ubuntu.com/release-notes/26.04/summary-for-lts-users/#software-updates-app)
