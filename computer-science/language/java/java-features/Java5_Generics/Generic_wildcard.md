# 泛型通配符

```md
所谓泛型通配，是指在声明泛型类型变量时，可以不必直接指定具体的泛型，而可以使用通配符来表示一系列类型。

Java 泛型通配符的出现是为了使 Java 泛型也支持向上转型，从而保持 Java 语言向上转型概念的统一。
但与此同时，也导致 Java 通配符出现了一些缺陷，使得其有特定的使用场景。
```
## 无边界
### 无限定通配符 <?>
```java
List<?> list1 = new ArrayList<String>();    // 合法
List<?> list2 = new ArrayList<?>();         // 不合法
List<String> list3 = new ArrayList<?>();    // 不合法
```
```md
对于带有通配符的引用变量，是不能调用具有与泛型参数有关的方法的。
```
```java
List<?> list1 = new ArrayList<String>();
list1.add(1);   // 编译不通过
list1.get(0);   // 编译通过
int size = list1.size();    // 由于size()方法中不含泛型参数，所以可以再通配符变量中调用
```

## 有边界
* 注意: 你可以为一个泛型指定上边界或下边界, 但是不能同时指定上下边界。

### 上界限定通配符 <? extends E>
```md
List<? extends 类型1> x = new ArrayList<类型2>();
类型2就只能是类型1或者是类型1的子类。

List<? extends Number> x = new ArrayList<Integer>(); // 由于Integer是Number的子类，这是合法的
List<? extends Number> x = new ArrayList<String>();  // 由于String不是Number的子类，这是不合法的

一旦执行了向上转型，将丢失掉向其中传递任何对象的能力，甚至 Object 也不行。
```
### 下界限定通配符 (超类型) <? super E>
```md
List<? super 类型1> x = new ArrayList<类型2>();
类型2就只能是类型1或者是类型1的超类。

List<? super Integer> x = new ArrayList<Number>();  // 由于Number是Integer的超类，这是合法的
List<? super Integer> x = new ArrayList<String>();  // 由于String不是Integer的超类，这是不合法的
```
* 那么到底什么时候使用下边界通配，什么时候使用上边界通配呢？
```md
首先考虑一下怎样才能保证不会发生运行时异常，这是泛型要解决的首要问题，
通过前面的内容可以看到，任何可能导致类型转换异常的操作都无法编译通过。

* 上边界通配
可以保证存放的实际对象至多是上边界指定的类型，
那么在读取对象时，我们总是可以放心地将对象赋予上边界类型的引用。

* 下边界通配
可以保证存放的实际对象至少是下边界指定的类型，
那么在存入对象时，我们总是可以放心地将下边界类型的对象存入泛型对象中。
```
### PECS法则
```md
如果你想从一个数据类型里获取数据，使用? extends通配符
如果你想把对象写入一个数据结构里，使用? super通配符
如果你既想存，又想取，那就别用通配符

这就是《Effective Java》书中所说的PECS法则（Producer Extends, Consumer Super）
```
```md
Collections工具类中的copy方法就完美地诠释了这个法则
public static <T> void copy(List<? super T> dest, List<? extends T> src) {}

这个方法的作用是将src列表完整地拷贝到dest列表中，
src是原始列表，我们需要读取其中的元素，所以它是生产者，需要使用extends通配；
dest是目标列表，需要将读取出来的元素存入这个列表中，所以他是消费者，使用super通配。
```
## 泛型 与 协变逆变
```md
泛型没有内建的协变类型。泛型中利用通配符实现的协变和逆变:

// 协变
List<? extends Fruit> flist = new ArrayList<Apple>();
// 逆变
List<? super Apple> alist = new ArrayList<Fruit>();
```
