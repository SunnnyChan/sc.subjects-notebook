# What Is Redis
```md
是一个由 Salvatore Sanfilippo 写的key-value存储系统。

Redis是一个开源的使用ANSI C语言编写、遵守BSD协议、支持网络、
可基于内存亦可持久化的日志型、Key-Value数据库，并提供多种语言的API。
```
* 场景
```md
主要在较小数据量的高性能操作和运算上
```
## Cases
* 最常用的就是会话缓存 Session Cache
* 全页缓存（FPC）
* 消息队列
```md
提供 list 和 set 操作，这使得Redis能作为一个很好的消息队列平台来使用
例如，Celery有一个后台就是使用Redis作为broker
```
* 活动排行榜或计数
```md
Redis在内存中对数字进行递增或递减的操作实现的非常好
```
* 发布、订阅消息(消息通知)
* 商品列表、评论列表等