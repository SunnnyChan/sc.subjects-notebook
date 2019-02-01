# What is RESTful
* REST (Representational State Transfer 表现层状态转换)
```md
Resource：资源，即数据（网络的核心），比如 goods，fruits 等；
Representational：某种表现形式，比如用 JSON，XML，JPEG等；
State Transfer：状态变化，通过 HTTP 动词实现。
```
```md
是Roy Thomas Fielding 博士于2000年在他的博士论文中提出来的一种万维网软件架构风格，
目的是便于不同软件/程序在网络（例如互联网）中互相传递信息。
```
```md
是一种对基于HTTP的应用设计风格，提供了一组设计原则和约束条件，而不是一种标准。
本质是基于HTTP协议对资源的增删改查操作做出定义。
```
## 背景
```md
真正推动REST发展的是移动互联网的出现。
由于多终端设备的兼容性需求，从前的服务端渲染已经很难满足要求了。

服务端不可能针对每一个Client渲染一套界面，如果服务端只提供需要的数据，
而具体界面的渲染完全交给具体的Client来完成，因此催生了REST的发展和普及。

RESTful可以通过一套统一的接口为 Web、iOS和Android提供服务，
另外对于很多平台来说（比如像Facebook，Twiter、微博、微信等开放平台），
它们不需要有显式的前端，只需要一套提供服务的接口，于是RESTful便是它们最好的选择。
```
* [参考 Web 架构 前后端分离](https://github.com/SunnnyChan/sc.study-notes/blob/master/computer-science/web/web-arch/WhatIs/README.md)
## Cases


## Cautions
```md
1. URL 只是表达被操作的资源位置，因此不应该使用动词，且注意单复数区分
2. 除了 POST 和 DELETE 之外，其他的操作需要幂等，例如对数据多次更新应该返回同样的内容
3. 设计风格没有对错之分，RESTful 一种设计风格，与此对应的还有RPC甚至自定义的风格
4. RESTful 和语言、传输格式无关
5. 无状态
  HTTP设计本来就是没有状态的，之所以看起来有状态因为浏览器使用了Cookies。
5. RESTful 没有定义 body 中内容传输的格式
  有另外的规范来描述怎么设计 body 的数据结构。
```

