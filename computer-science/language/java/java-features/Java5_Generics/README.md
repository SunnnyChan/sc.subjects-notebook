# Java Generics
```md
是将类型参数化，其在编译时才确定具体的参数。
是一种编译器机制，会得到方便代码重用的代码模板。

* 泛型只存在于编译阶段，而不存在于运行阶段
在编译后的 class 文件中，是没有泛型这个概念的。

* 泛型优势
可以在编译时发现类型不匹配的错误，并且取数据时不需要手动强转类型。
减少了代码的复杂性：避免了在代码中使用强制类型转换的麻烦。
增强了代码的安全性：将运行时异常“ClassCastException”转到了编译时检测异常。
```
* 类型参数
```md
类型参数（又称类型变量）用作占位符，指示在运行时为类分配类型。
根据惯例，类型参数是单个大写字母，该字母用于指示所定义的参数类型。

推荐的标准类型参数：

E：元素
K：键
N：数字
T：类型
V：值
S、U、V 等：多参数情况中的第 2、3、4 个类型
```
* Java 泛型 vs C++ 泛型
```md
泛型思想最早在C++语言的模板（Templates）中产生，Java后来也借用了这种思想。
虽然思想一致，但是他们的实现存在着本质的不同。

C++中的模板是真正意义上的泛型，在编译时就将不同模板类型参数编译成对应不同的目标代码，
ClassName<String>和ClassName<Integer>是两种不同的类型，这种泛型被称为真正的泛型。
这种泛型实现方式，会导致类型膨胀，因为要为不同具体参数生成不同的类。

Java中的ClassName<String>和ClassName<Integer>虽然在源代码中属于不同的类，
但是编译后的字节码中，他们都被替换成原始类型ClassName，而两者的原始类型是一样的，
所以在运行环境中，ClassName<String>和ClassName<Integer>就是同一个类。

Java中的泛型是一种特殊的语法糖，通过类型擦除实现，这种泛型称为伪泛型。
由于Java中有这么一个障眼法，如果没有深入研究，就会产生莫名其妙的问题。
```
* 类型擦除 （type erasure）
```md
使用泛型的时候加上的类型参数，会在编译的时候去掉，这个过程就称为类型擦除。
泛型附加的类型信息对JVM来说是不可见的。

Java编译器会在编译时尽可能的发现可能出错的地方，
但是仍然无法避免在运行时出现类型转换异常的情况。

类型擦除也是 Java的泛型实现方法 与 C++模版机制实现方式 之间的重要区别。
```
* * 很多泛型的奇怪特性都与这个类型擦除的存在有关
```md
1. 泛型类并没有自己独有的 Class 类对象
  比如并不存在 List<String>.class 或是 List<Integer>.class，而只有 List.class。
2. 静态变量是被泛型类的所有实例所共享的
  对于声明为 MyClass<T> 的类，访问其中的静态变量的方法仍然是 MyClass.myStaticVar。
  不管是通过 new MyClass<String> 还是 new MyClass<Integer> 创建的对象，都是共享一个静态变量。
3. 泛型的类型参数不能用在 Java 异常处理的 catch 语句中
  因为异常处理是由 JVM 在运行时刻来进行的。
  由于类型信息被擦除，JVM 是无法区分两个异常类型 MyException<String> 和 MyException<Integer> 的。
  对于 JVM 来说，它们都是 MyException 类型的。也就无法执行与异常对应的 catch 语句。
```
* 原始类型（raw type）
```md
是擦除去了泛型信息，最后在字节码中的类型变量的真正类型。

无论何时定义一个泛型类型，相应的原始类型都会被自动地提供。
类型变量被擦除，并使用其限定类型（无限定的变量用Object）替换。
```
* 泛型类
```md
泛型类一般使用 T 作为泛型的标志。
在需要使用 Map 的类中，通常使用 K V 两个字母表示 Key Value 对应的类型。
```
* 泛型方法
```md
泛型方法一般使用 T 作为泛型的标志。
```
```
public class GenericMethod<T> {
    public <T> void sayHi(T t){
        System.out.println("Hi "+t);
    }
}

String i="abc";
new GenericMethod<Integer>().<String>sayHi(i);
```
```md
泛型方法有自己的类型参数，泛型类的成员方法使用的是当前类的类型参数。
方法中有<T> 是泛型方法；没有的，称为泛型类中的成员方法。
```
## [泛型通配符](Generic_wildcard.md)

## 泛型与继承
```md
引用的参数类型与实际对象的参数类型要保持一致（通配符除外），就算两个参数类型是继承关系也是不允许的。

看看下面两行代码，它们均不能通过编译:
ArrayList<String> arraylist1 = new ArrayList<Object>();
ArrayList<Object> arrayList2 = new ArrayList<String>();
```
## 泛型与多态
```md
普通类型的多态是通过继承并重写父类的方法来实现的，泛型也不例外。
```
```java
public class Father<T> {
    public void set(T t) {
        System.out.println("I am father, t = " + t);
    }

    public T get() {
        return null;
    }
}

public class Son extends Father<String> {
    @Override
    public void set(String s) {
        super.set(s);
        System.out.println("I am son");
    }

    @Override
    public String get() {
        return super.get();
    }

    public static void main(String[] args) {
        Father<String> father = new Son();
        father.set("hello world");
    }
}
```
```md
从字节码中可以看到，除了void set(String)和String get()两个方法以外，
还出现了void set(Object)和Object get()两个方法，这两个方法在Son源代码里并不存在，
这是编译器为了解决泛型的多态问题而自动生成的方法，称为”桥方法”。

这两个方法的签名与Father类中的两个方法的签名完全一致，这才是真正的方法重写。
也就是说，子类真正重写的是我们看不到的桥方法。
```

## 参考
* [泛型原理](https://blog.wangqi.love/articles/Java/%E6%B3%9B%E5%9E%8B%E5%8E%9F%E7%90%86.html)
* [Java 泛型详解](https://www.manuu.vip/2017/07/30/Java-Generics/)

* [示例代码](Generic.java)