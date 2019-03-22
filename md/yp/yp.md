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

* 压测平台
* RPC
* 配置系统
* 服务注册
* 路由网关
* 日志系统
* 监控系统

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

![加入mibench](https://i.imgur.com/FiUJUXi.png)


<slide :class="aligncenter">
## 有品 dubbo - RPC
----

<slide>

* 优化泛化调用
* 支持内部网关
* 支持外部网关
* nacos 注册中心
* 支持业务错误码
* 统一结果输出格式
* 接入 zander
* traceid
* 性能优化

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
![](https://i.imgur.com/avoBFvO.png)


<slide :class="aligncenter">
## 有品 nacos - 服务治理
----

<slide :class="aligncenter">
![](https://i.imgur.com/7xVqPQM.png)

<slide>

* 服务注册 治理平台
* 高效访问 解耦

<slide :class="aligncenter">

![](https://i.imgur.com/76pLCIm.png)


<slide :class="aligncenter">
## 业务网关(产品站)
----

* 逻辑收敛、内容可裁剪、可并发

<slide :class="aligncenter">
## 有品 gateway - 网关
----

* 采用 API Gateway 可以与微服务注册中心连接，实现微服务无感知动态扩容
* API Gateway 对于无法访问的服务，可以做到自动熔断，无需人工参与
* API Gateway 可以方便的实现蓝绿部署，金丝雀发布或 A/B 发布
* API Gateway 做为系统统一入口，我们可以将各个微服务公共功能放在 API Gateway 中实现，以尽可能减少各服务的职责
* 帮助我们实现客户端的负载均衡策略

<slide :class="aligncenter">

![](https://i.imgur.com/nD6aa1a.png)

<slide>

* 流量控制
* 服务路由
* 数据缓存
* 协议转换
* 服务注册与发现
* 负载均衡
* 日志记录

<slide :class="aligncenter">
## 监控系统 - owl
----

* 实时分析: 深入分析系统日志，通过Flink进行数据处理与计算
* 报警定制: 建立了和有品办公IM的通信通道，报警信息能够直接发送到有品企业微信的相关负责人和群聊
* 上线预警: 预置上线预警功能。当系统上线或上线代码更新时，当错误日志数量超过阈值时会开启报警，对上线行为进行提醒
* 运行分析: 对系统运行状态进行计算分析，并通过运行图的方式进行展示


<slide>
## 服务化架构

<slide :class="aligncenter">
![架构图](https://i.imgur.com/PApcS4t.png)

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
