# 第 12 节　安装其他 Linux 发行版时，怎样选 VMware 客户机类型

VMware 的“客户机操作系统”选项用来为虚拟机选择合适的默认配置。实际装入哪个发行版由安装镜像决定。课中用 CentOS 和 Kali 演示了怎样选类型，向导停在选择页，没有启动安装。

## 在向导里怎么选

1. **先认准镜像。** 在发行版官网确认产品名称、版本和架构。例如 CentOS Linux 和 CentOS Stream 是两条不同的发行线；普通 Intel/AMD 64 位 PC 镜像常标为 `x86_64` 或 `amd64`，ARM64 是另一种架构。
2. **找同名项。** 课中入口是 **Workstation 16 → 文件 → 新建虚拟机 → 典型（推荐）→ 稍后安装操作系统 → Linux → 版本**。有同名项时按发行版主版本和镜像架构匹配。例如旧 CentOS Linux 8 的 x86_64 镜像，对应当时列表中的 **CentOS 8 64 位**。选好后收起下拉框，核对“版本”栏实际显示的值。
3. **没有同名项时，查官方虚拟化指南。** 例如 Kali 的官方 VMware 指南要求选择 **Linux → 向导提供的最新 Debian 版本**，位数与镜像一致。Kali 的上游是持续更新的 **Debian Testing**；一篇旧教程里出现的 Debian 稳定版编号，不能用来确定 Kali 的基础版本。[Kali 的 VMware 客户机指南](https://www.kali.org/docs/virtualization/install-vmware-guest-vm/) · [Kali 与 Debian 的关系](https://www.kali.org/docs/policy/kali-linux-relationship-with-debian/)
4. **核对通用 Linux 选项。** 如果没有合适的发行版预设，再查目标镜像的发行说明，把内核系列和架构与 **其他 Linux…内核** 条目比对。通用项是候选配置，能否完成安装还要通过启动镜像验证。

## 别把三种版本号混在一起

| 视频里的数字 | 它表示什么 | 对选择的意义 |
| --- | --- | --- |
| Kali 2020.4 | Kali 的镜像发布版本 | 用它查这一次发布的说明。 |
| Linux 5.9.0 | 该镜像使用的 Linux 内核版本 | 讲师据此指向 Workstation 16 的“其他 Linux 5.x 及更高版本内核 64 位”。 |
| Debian 10.x 64 位 | 演示里实际选中的 VMware 客户机预设 | 关闭向导前字段仍为这个值。讲师也指过 Debian 9.x，但搜索摘要里的 Debian 9 说的是某个软件的安装说明。 |

## 到哪里找镜像

- **CentOS 下载页**目前提供 CentOS Stream 9 和 10。若要复现课中的 **8 (2011)**，可到 Vault 找 CentOS Linux **8.3.2011**。CentOS Linux 8 已于 **2021 年 12 月 31 日**结束维护。[CentOS 下载](https://www.centos.org/download/) · [8.3.2011 x86_64 镜像归档](https://vault.centos.org/8.3.2011/isos/x86_64/) · [CentOS Linux 8 生命周期](https://www.centos.org/centos-linux-eol/)
- **Kali 下载页**提供两种与本课有关的镜像。自行安装选 **Get Kali → Installer Images** 获取 ISO，使用预装好的 VMware 虚拟机则选 **Virtual Machines**。发行历史可核对每次发布配套的内核。截至 2026-11-19，最新一项为 **Kali 2026.3、Linux 7.1**，课中的 5.x 属于 2020.4。[Kali 官方下载](https://www.kali.org/get-kali/) · [Kali 发行历史](https://www.kali.org/releases/)
- **Arch Linux 官网**介绍了它简洁、轻量的设计取向，并提供文档和下载入口。讲师只浏览了首页。[Arch Linux 官网](https://archlinux.org/)

## 自己装完后怎么核对

从虚拟硬盘启动并登录新系统后，在客户机终端运行以下命令。这是跟做时的检查方法，视频中没有执行。

```bash
cat /etc/os-release
uname -r
uname -m
```

依次核对发行版身份、当前运行的内核、体系架构。第一项看 `PRETTY_NAME` 或 `ID`。将三项分开记录，之后比较不同发行版时就能复用。
