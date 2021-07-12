---
layout: post
title: RabbitMq工作模式深度剖析
date: 2021-07-12
tags: All About Java
---

## RabbitMq工作模式深度剖析

### MQ的优势

1、应用解耦。应用的之间的数据存取，依赖于mq，使得微服务之间的各个应用耦合性降低，提升了容错性和可维护性。

2、异步提速。提升了用户的体验以及系统的吞吐量。

3、削峰填谷。利用mq将系统的并发量提高，然后系统从mq中异步取出数据进行处理，提高了系统的稳定性。

### MQ的劣势

1、系统的可用性降低。系统之间依赖于MQ，MQ一旦宕机，服务之间就无法交互。

2、系统的复杂度提高。使用MQ之前，服务之间是同步进行调用；使用MQ之后，服务之间是异步调用。

### MQ简介

基于AMQF协议（高级消息队列协议），相关概念：

1、Broker，接受和分发消息的应用。

2、Virtual host，虚拟的分组，可以划分多个。

3、Connection，生产者、消费者和broker之间的TCP链接。

4、Channel，轻量级的Connection，极大减少了操作系统之间建立TCP的connection的开销。

5、Exchange，message到达broker的第一站，根据分发规则，匹配查询表中的route key，将消息分发到queue中。

6、Queue，消息最终存放的地方，消费者会在这里将消息获取。

7、Binding，Exchange和Queue之间的虚拟链接，包含route key，Binding信息将会被保存到exchange中的查询表中，用于message的分发依据。

### RabbitMq的6种工作模式

1、简单模式

2、work queues

3、Publish/Subscribe发布与订阅模式

4、Routing路由模式

5、Topics主题模式

6、RPC远程调用模式

