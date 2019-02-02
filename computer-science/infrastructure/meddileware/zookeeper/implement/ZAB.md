# ZAB 协议
* Broadcast
```md
Zookeeper 常规情况下更新数据的时候，由 Leader 广播到所有的 Follower。
```
* 三种节点状态
```md
Looking：选举状态。
Following：Follower 节点（从节点）所处的状态。
Leading：Leader 节点（主节点）所处状态。
```
* 崩溃恢复
> * Leader election

> * Discovery

> * Synchronization
