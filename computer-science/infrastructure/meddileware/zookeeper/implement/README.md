# ZK 实现

## Data Model - 数据模型
* Znode
```md
ZooKeeper 的数据存储 基于称为 Znode 的节点。
Znode 的引用方式是路径引用，类似于文件路径。
```
> * 组成
```md
data：Znode 存储的数据信息。
ACL：记录 Znode 的访问权限，即哪些人或哪些 IP 可以访问本节点。
stat：包含 Znode 的各种元数据，比如事务 ID、版本号、时间戳、大小等等。
child：当前节点的子节点引用，类似于二叉树的左孩子右孩子。
```

## Watch - 事件通知
```md
注册在特定 Znode 上的触发器。
当这个 Znode 发生改变，将会触发 Znode 上注册的对应事件，请求 Watch 的客户端会接收到异步通知。
```

##  一致性
* [ZAB 协议](ZAB.md)

