# Java 语言特性

* [Java Exception](java-language-features/Exception.md)
* [Java Reflect](java-language-features/Reflect.md)

## Java 11
* 支持 Unicode 10.0
* 标准化 TTP Client
* 编译器线程的延迟分配
```md
1. 添加了新的命令-XX:+UseDynamicNumberOfCompilerThreads动态控制编译器线程的数量
```
* 新的垃圾收集器 — ZGC （一种可伸缩的低延迟垃圾收集器(实验性)）
* Epsilon - 一款新的实验性无操作垃圾收集器
```md
1. Epsilon GC 只负责内存分配，不实现任何内存回收机制。这对于性能测试非常有用，可用于与其他GC对比成本和收益。
```
* Lambda 参数的局部变量语法
```md
Java10中引入的var字段得到了增强，现在可以用在lambda表达式的声明中。
如果lambda表达式的其中一个形式参数使用了var，那所有的参数都必须使用var。
```

## Java 10
* Local-Variable Type Inference （局部变量类型推断）- var 保留类型名称
* Optional 类添加了新的方法 orElseThrow - 相比于已经存在的get方法，这个方法更推荐使用。

## Java 9
* Java Platform Module System
* 支持私有接口方法
* 交互式命令行控制台
* diamond语法与匿名内部类结合使用
* 下划线_不能单独作为变量名使用
* Javadoc 优化
```md
1. 简化Doclet API
2. 支持生成HTML5格式
3. 加入了搜索框，使用这个搜索框可以查询程序元素、标记的单词和文档中的短语。
4. 支持新的模块系统。
```
* JVM 优化
```md
1. 增强了Garbage-First(G1)并用它替代Parallel GC成为默认的垃圾收集器。
2. 统一了JVM 日志，为所有组件引入了同一个日志系统。
3. 删除了JDK 8中弃用的GC组合。（DefNew + CMS，ParNew + SerialOld，Incremental CMS）。
```
* properties文件支持UTF-8编码，之前只支持ISO-8859-1
* 支持Unicode 8.0，在JDK8中是Unicode 6.2

## Java 8
* [Default Methods](Java8_Default-Methods.md)
* [Lambda Expressions]()
* [Stream API]()
* Method references
* Repeating Annotations 
* Type Annotation
* 类型推断增强
* Method Parameter Reflection
* HashMap 优化
* Date Time API
* java.util 包优化
* java.util.concurrent 包优化
* HotSpot 优化

## Java 7
* 二进制前缀 0b 或者 0B
* switch 支持 String 类型
* 泛型实例化类型自动推断
* try-with-resources
* 单个catch中捕获多个异常类型（用 | 分割)

## Java 6
* JDBC4.0规范
* 集合框架增强
* Scripting - 让其他语言在java平台上运行

## Java 5
* [Generics](Java5_Generics/README.md)
* [Typesafe Enums]()
* [Annotation]()
* Varargs （可变参数）
* Static Import （静态导入）
* java.util.concurrent
