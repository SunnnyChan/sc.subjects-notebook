# Apache ZooKeeper
## [What Is?](WhatIs.md)

## Design
```md
ZooKeeper 是为读多写少的场景所设计。
Znode 并不是用来存储大规模业务数据，而是用于存储少量的状态和配置信息，每个节点的数据最大不能超过 1MB。
```

## [Implement](implement/README.md)
* Data Model

## Utility
* 分布式锁
```md
这是雅虎研究员设计 ZooKeeper 的初衷。
利用 ZooKeeper 的临时顺序节点，可以轻松实现分布式锁。
```
* 服务注册和发现
```md
利用 Znode 和 Watcher，可以实现分布式服务的注册和发现。
最著名的应用就是阿里的分布式 RPC 框架 Dubbo。
```
* 共享配置和状态信息
```md
Redis 的分布式解决方案 Codis，就利用了 ZooKeeper 来存放数据路由表和 codis-proxy 节点的元信息。
同时 codis-config 发起的命令都会通过 ZooKeeper 同步到各个存活的 codis-proxy。

此外，Kafka、HBase、Hadoop 也都依靠 ZooKeeper 同步节点信息，实现高可用。
```

## Develop
* [API](dev/API.md)
