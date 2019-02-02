# MQ 技术选型

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