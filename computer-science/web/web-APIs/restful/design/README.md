# RESTful API Design

## HATEOAS (Hypermedia As The Engine Of Application State 超媒体应用程序状态的引擎)
```md
RESTful 和JSONAPI 部分都贯穿了HATEOAS思想。
实际上 HATEOAS 算作被JSON API定义了的一部分。
```
* 思想
```md
既然 RESTful 是利用 HTTP 协议来进行增删改查，那怎么在没有文档的情况下找到这些资源的地址呢?
一种可行的办法就是在 API 的返回体里面加入导航信息，也就是links。
这样就像 HTML 中的 A 标签实现了超文本文档一样，实现了超链接JSON文档。
```