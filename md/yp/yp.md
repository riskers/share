title: 有品电商技术演进
speaker: 张志勇

<slide :class="aligncenter">
# 有品电商技术演进
# 从单体 server 到分布式架构演进
----

### 张志勇

<slide :class="aligncenter">
## 单体架构

<slide :class="aligncenter">
![](https://i.imgur.com/ceAqKmQ.png)

:::note
甚至不能说是『架构』
接下来是面临的问题
:::

<slide>
### 研发成本
----

* 代码重复率高
* 需求变更困难
* 无法满足新业务快速迭代

<slide>
### 运维效率
----

* 测试、部署成本高
* 可伸缩性差
* 可靠性差

<slide>
## 解决策略
-----

* 拆分
* 解耦
* 独立
* 分层

<slide>

* 压测平台\: mibench
* RPC\: dubbo
* 配置系统 + 服务注册\: nacos
* 路由网关\: gateway
* 日志系统

:::note
这些是我们在过去一年对旧系统的改造
:::

<slide :class="aligncenter">
## mibench - 压测平台

<slide image="https://i.imgur.com/NAX2vSV.png">

<slide>

* 部署便捷
* 性能瓶颈
* 使压测可重放
* 具备一定的业务压测

<slide>

* 智能 QPS 控制
* 压测性能好于任何一个被压测接口

<slide :class="aligncenter">

![](https://i.imgur.com/dA36z9X.png)

<slide>

* 服务器无状态
* 生成报告、存档

<slide>

![](https://i.imgur.com/NGJafQn.png)

<slide>

* 具备调试、权限管理

<slide :class="aligncenter">

![](https://i.imgur.com/MZaEOOJ.png)

<slide>

* 系统可支持水平扩展
* Agent 服务治理

<slide :class="aligncenter">

![](https://i.imgur.com/FiTYHXJ.png)

<slide :class="aligncenter">
### 365{.text-data}

服务 365 个接口

:::note
上线一年 365 个接口
:::

<slide :class="aligncenter">
### 3500{.text-data}

产出 3500 份测试报告

:::note
上线一年 3500 份测试报告
:::

<slide :class="aligncenter">

![](https://i.imgur.com/3XmHShC.png)


<slide :class="aligncenter">
## dubbo - RPC
----

<slide>

* 泛化调用
* gateway 调用
* 统一结果输出格式
* 接入 zander

<slide :class="aligncenter">
### 219{.text-data}

219 个 provider 实例

:::note
219 个 provider 实例
:::

<slide :class="aligncenter">
### 353{.text-data}

353 个 consumer 实例

:::note
353 个 consumer 实例
:::

<slide :class="aligncenter">
![](https://i.imgur.com/GfAgwR8.png)


<slide :class="aligncenter">
## nacos - 服务拆分
----

<slide :class="aligncenter">
![](https://i.imgur.com/7xVqPQM.png)

<slide>

* 服务注册 治理平台
* 高效访问 解耦
* 逻辑收敛、内容可裁剪、可并发

<slide :class="aligncenter">

![](https://i.imgur.com/GILxsPb.png)


<slide :class="aligncenter">
## gateway - 网关
----

* 将各系统对外暴露的服务聚合起来，所有要调用这些服务的系统都需要通过 API 网关进行访问
* 基于这种方式网关可以对 API 进行统一管控

<slide :class="aligncenter">

![](https://i.imgur.com/4J0nYXP.png)

<slide>

* 熔断
* 灰度测试
* 限流

<slide :class="aligncenter">

![](https://i.imgur.com/MMklxR2.png)

<slide>
## 服务化架构

<slide :class="aligncenter">
![](https://i.imgur.com/HiiJiej.png)

:::note
经过上面的改造，这是现在的架构
:::

<slide class="bg-black" :class="size-80 bg-black-blue" image="https://source.unsplash.com/6njoEbtarec/ .dark">

* 使用怎样的技术需要根据团队的技术水平和技术发展的阶段进行取舍
* 没有完美的架构,只有**合适**的架构

<slide :class="aligncenter">
## Thanks

<slide :class="aligncenter">
## Q&A
