# MQ 实现

## 开源实现
* [Apache Kafka](../../../bigdata/components/kafka/README.md)
* [Apache Pulsar] - 由Yahoo开发并开源的下一代发布订阅消息系统
* [Apache DistributedLog] - 被称为“共享日志基础设施”

* [Apache RocketMQ] - RocketMQ是阿里开源的消息中间件
* [RabbitMQ] - RabbitMQ是基于Erlang语言编写的开源消息队列
* [ActiveMQ] - ActiveMQ介于ZeroMQ和RabbitMQ之间,被誉为消息中间件的“瑞士军刀”
* [MetaQ](https://github.com/killme2008/Metamorphosis) - 淘宝开源的一个Java消息中间件，类似apache-kafka
* [NSQ - A realtime distributed messaging platform](x_NSQ.md)

* [Apollo] - Apache 称 Apollo 为最快、最强健的STOMP服务器

* [ZeroMQ] - 是一个异步消息库，在套接字的基础上提供了类似于消息代理的机制
* [nanomsg] - 构建在ZeroMQ的可靠性能之上，同时又提供了若干重要的改进

## 技术选型
* [NSQ vs Kafka](http://bridgeforyou.cn/2018/10/02/Nsq-5-Nsq-vs-Kafka/)

* 协议
```md
RabbitMQ 支持 AMQP（二进制），STOMP（文本），MQTT（二进制），HTTP（里面包装其他协议）等协议。
Kafka 使用自定义协议。
```
* 性能
```md
RabbitMQ 在有大量消息堆积的情况下性能会下降，Kafka不会。
毕竟AMQP设计的初衷不是用来持久化海量消息的，而Kafka一开始是用来处理海量日志的。
```
* 总体
```md
ZeroMQ小而美，RabbitMQ大而稳，Kakfa和RocketMQ快而强劲。
```