title: 有品电商技术演进
speaker: 张志勇
theme: tomorrow

<slide :class="aligncenter">
# 有品电商技术演进
# 从单体 server 到分布式架构演进
----

### 张志勇

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
## 服务化架构
----

<slide :class="aligncenter">
![](https://i.imgur.com/HiiJiej.png)

<slide>

* 拆分
* 解耦
* 独立
* 分层

<slide>

* 压测平台\: mibench
* 路由网关\: gateway
* 日志系统
* 配置系统 + 服务注册\: nacos
* RPC\: dubbo

<slide>
## mibench - 压测平台
------

![](https://i.imgur.com/NAX2vSV.png)


<slide>

* 了解性能瓶颈
* ...

<slide>
## dubbo - RPC
----

详见[wiki](https://wiki.n.miui.com/display/MIOTStore/dubbo-demo)

<slide>
## nacos - 服务拆分
----

![](https://i.imgur.com/7xVqPQM.png)

<slide>

* 服务注册 治理平台
* 高效访问 解耦
* 逻辑收敛、内容可裁剪、可并发

<slide>

详见[wiki](https://wiki.n.miui.com/display/MIOTStore/dubbo-demo)

<slide>
## gateway - 网关
----

将各系统对外暴露的服务聚合起来，所有要调用这些服务的系统都需要通过 API 网关进行访问，基于这种方式网关可以对 API 进行统一管控

![](https://i.imgur.com/4J0nYXP.png)

<slide>

* 熔断
* 灰度测试
* 限流
