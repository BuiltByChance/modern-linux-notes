# 第 4 节　开源一定免费吗？

**开源软件可以收费，也可以用于商业项目。** 想知道能否使用、修改和再分发代码，要读软件的开源许可证。想知道使用某个发行版要花多少钱、出了问题谁来处理，要看供应商提供的订阅。开源软件本身可以出售，维护和技术支持也可以收费。[开放源代码促进会 FAQ](https://opensource.org/faq#commercial)

## 用红帽企业 Linux（RHEL）判断费用

课上用个人学习和企业服务器作对比。实际选 RHEL 订阅时，先弄清谁在使用、机器用于开发测试还是生产、需要多少个实例，以及遇到故障时是否需要红帽工程师协助。

| 使用场景 | 官方方案与适用范围 |
| --- | --- |
| 个人学习，或自己运行小规模生产服务 | 个人可申请免费的开发者订阅，最多 **16 个物理或虚拟节点**，可用于开发、测试及条款允许的个人小规模生产。订阅含更新和勘误，技术问题采用自助支持。[个人订阅 FAQ](https://developers.redhat.com/articles/faqs-no-cost-red-hat-enterprise-linux) · [RHEL 官方下载](https://developers.redhat.com/products/rhel/download) |
| 在公司为业务开发、测试应用 | **RHEL for Business Developers** 为每位注册用户提供最多 **25 个物理、虚拟或云实例**，免费用于企业开发和测试。应用上线时，要按生产用途另行确认订阅。[红帽企业开发者计划](https://developers.redhat.com/products/rhel/business) |
| 企业生产系统需要持续维护或厂商支持 | 核对订阅涵盖的部署数量、软件更新、安全修复和支持级别。若需要人工处理故障，还应查看支持时段和响应承诺。[红帽订阅模式说明](https://www.redhat.com/zh-cn/about/subscription-model-faq) · [RHEL 订阅指南](https://www.redhat.com/en/resources/red-hat-enterprise-linux-subscription-guide) |

例如，同一个应用可以先在公司的免费开发测试环境里验证，再部署到生产服务器。两台机器运行同一款 RHEL，但用途发生了变化，开发测试订阅的适用范围止于前一阶段。

## 比较发行版时记什么

讲师把 Ubuntu、CentOS、Red Hat 和 Kali 放在一起，希望学会一种之后能说出其余几种的共同点和差异。复习时可以从安全更新和故障支持入手。为每个发行版记下谁提供安全更新、出了问题去哪里求助，以及是否有厂商承诺响应。
