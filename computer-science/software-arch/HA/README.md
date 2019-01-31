# 高可用架构

* [HA](HA.md)

## 策略
* [流量](traffic/README.md)
* [服务]
* [监控](monitor/README.md)

## 组件
* [Sentinel](https://github.com/alibaba/Sentinel/wiki/%E4%BB%8B%E7%BB%8D)
* [Hystrix](https://github.com/Netflix/Hystrix)

### Sentinel vs Hystrix
```md
* Hystrix
以隔离和熔断为主的容错机制

* Sentinel
多样化的流量控制
熔断降级
系统过载保护
实时监控和控制台
```
* [Sentinel vs Hystrix](https://www.jianshu.com/p/d1f22a555065)

## 参考
* [可伸缩架构 : 面向增长应用的高可用](https://github.com/SunnnyChan/SunnnyChan.github.io/blob/master/post/readme/reading/arch/scalable_arch/README.md)
* [分布式服务框架：原理与实践](https://github.com/SunnnyChan/SunnnyChan.github.io/blob/master/post/readme/reading/arch/DS-Service-Framework/README.md)