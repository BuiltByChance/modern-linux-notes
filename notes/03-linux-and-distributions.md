# 第 3 节　认识 Linux · Unix、开源与发行版

下载 Ubuntu 时，拿到的是一套可以安装的操作系统。它把 Linux **内核**和系统工具、软件包、安装程序等组合起来，形成一个**发行版**。内核负责调度进程、管理内存和设备。桌面上看到的窗口、菜单和应用中心属于上层软件，例如 Ubuntu Desktop 集成了 GNOME 桌面。[Red Hat 对发行版的说明](https://www.redhat.com/en/topics/linux/whats-the-best-linux-distro-for-you) · [Ubuntu Desktop](https://ubuntu.com/download/desktop)

## Unix 和 Linux 是什么关系

- **1969 年**，Ken Thompson、Dennis Ritchie 等人在贝尔实验室开始开发 Unix。早期实现使用汇编，1973 年 Unix 内核用 C 重写，1974 年发表了介绍 Unix 的论文。[Ritchie 对 Unix 早期历史的回顾](https://www.nokia.com/bell-labs/about/dennis-m-ritchie/hist.html)
- **1991 年**，Linus Torvalds 公开了早期 Linux 内核源码。Linux 借鉴 Unix 的设计，从头实现了类 Unix 内核，后来由众多开发者共同维护。**1994 年**发布了 Linux 1.0。读到“像 Unix”时，应理解为系统设计和接口上的联系。[Linux 内核文档](https://docs.kernel.org/admin-guide/README.html) · [首次发布回顾](https://www.linuxfoundation.org/blog/blog/anniversary-of-first-linux-kernel-release-a-look-at-collaborative-value) · [内核 1.0 发布档案](https://www.kernel.org/pub/linux/kernel/v1.0/)

## 为什么同一份源码能发展出不同产品

判断一个项目是否开源，要看能否取得源码，以及许可证是否允许使用、修改和再分发。开发者可以报告问题、提交修正，由维护者决定是否纳入后续版本。开源软件也可以商用、收费或提供付费支持。[开放源代码促进会的定义](https://opensource.org/osd)

Android 是课上的类比。它使用基于 Linux 的内核，厂商可以在 Android 开源项目（AOSP）基础上定制界面、动画和预装应用，因此手机外观不同也可能有共同基础。判断某个组件是否开源，要看该组件自身的许可证。[AOSP 概览](https://source.android.com/docs/setup/about) · [Android 内核说明](https://source.android.com/docs/core/architecture/kernel)

## 课上四个名称的区别

| 课上写的名称 | 复习时怎么区分 |
| --- | --- |
| Ubuntu | 讲师以个人桌面为例，课程建议先用它熟悉 Linux。Ubuntu Desktop 提供图形桌面和应用中心，Ubuntu 也有服务器版本。[桌面版](https://ubuntu.com/download/desktop) · [服务器版](https://ubuntu.com/download/server) |
| CentOS | 视频讲的是企业服务器上曾常见的 **CentOS Linux**，它根据已发布的 RHEL 重建。CentOS Linux 7 已于 2024 年 6 月 30 日结束维护。今天项目提供 **CentOS Stream**，在 RHEL 上游开发、测试后续版本可能纳入的改动。[项目说明](https://www.centos.org/cl-vs-cs/) · [CentOS Stream 下载](https://centos.org/download/) |
| Red Hat | 板书用的是公司名。对应的企业发行版是 **Red Hat Enterprise Linux（RHEL）**，企业可以订阅更新和技术支持。[RHEL 产品说明](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux) |
| Kali | 基于 Debian，面向安全审计和数字取证，预装的软件围绕这些任务组织。[Kali 官方介绍](https://www.kali.org/docs/introduction/what-is-kali-linux/) |

视频提到桌面软件时，用 QQ 的安装难度举例。现在腾讯直接提供 Linux 版 QQ。在 Ubuntu 上可按机器的处理器架构选择对应的 `.deb` 包。[腾讯 QQ Linux 版下载](https://im.qq.com/linuxqq/index.shtml)

## 上机自查（课后补充）

有 Linux 终端时，可以分别查看发行版和正在运行的内核。视频中的讲师用记事本列举名称，以下是课后练习。

| 想查什么 | 命令 | 看哪里 |
| --- | --- | --- |
| 这套系统叫什么？ | `cat /etc/os-release` | 看 `PRETTY_NAME`，通常能读到发行版名称和版本。 |
| 当前运行哪个内核？ | `uname -r` | 输出内核发行号，可能附带发行版打包时加的后缀。 |

例如，给 Ubuntu 安装新内核并重启进入该内核后，`uname -r` 会显示新的内核发行号，发行版名称仍是 Ubuntu。[os-release 字段说明](https://freedesktop.org/software/systemd/man/latest/os-release.html) · [GNU uname 手册](https://www.gnu.org/software/coreutils/manual/html_node/uname-invocation.html)
