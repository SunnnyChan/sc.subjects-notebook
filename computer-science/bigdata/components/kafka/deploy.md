# Kafka 部署

## 单机安装
```sh
$ wget https://archive.apache.org/dist/kafka/0.10.0.0/kafka_2.11-0.10.0.0.tgz
```
* 启动 内置 zookeeper
```sh
$ nohup sh  bin/zookeeper-server-start.sh config/zookeeper.properties &
```
* 启动 kafka
```sh
$ nohup bin/kafka-server-start.sh config/server.properties &
```
* 创建 topic
```sh
$ bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic test
$ bin/kafka-topics.sh --list --zookeeper localhost:2181
test
```
* 发送消息
```sh
$ bin/kafka-console-producer.sh --broker-list localhost:9092 --topic test
This is a message
This is another message
```
* 消费消息
```sh
$  bin/kafka-console-consumer.sh --zookeeper localhost:2181 --topic test --from-beginning
This is a message
This is another message
```