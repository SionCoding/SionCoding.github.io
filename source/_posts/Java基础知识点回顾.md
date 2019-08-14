title: Java 基础知识点回顾
author: Sion
tags:
  - JavaSE
  - Java 基础
categories:
  - 技术
date: 2019-07-16 10:03:00
---
## Java基础

### JDK和JRE区别
1. `jre`即Java Runtime Environment，Java运行环境。包括Java虚拟机和Java类库
2. `jdk`是Java开发工具包，例如：`tools.jar`

<!-- more -->

### == 和 equals 区别
1. `==`是一个比较运算符，对于基本类型，比较的是具体的数值(int、double..)；对于引用类型，比较的是对象的内存地址
2. `equals`是超类`Object`就具有的方法，因此所有的引用类型都具有这个方法，只用用来比较引用数据类型。`equals`方法默认比较的对象内存地址，如果重写该方法，一般比较的是对象的属性值

### final的作用
可修饰类，类属性，类方法。
1. 被`final`修饰的类不能被继承
2. `final`修饰的类属性可以是基本类型也可以是引用类型，如果是基本类型就不能再被赋值，如果是引用类型，则不能再指向其他引用地址，但对象本身是可以被改变的。

```java
public class FinalTest {

    private static final User USER = new User();

    public static void main(String[] args) {
        User u2 = new User();
//        user = u2; // ERROR
        USER.age = 23;
    }
}

class User {
    int age = 12;
}
```
3. 类中所有`private`方法都是隐式地定义为final，为private方法添加final多此一举

### String属于基本类型吗
#### 不，String属于特殊的引用类型

Java中属于基本类型的有：int、short、long、char、boolean、float、double、byte
1. `String`是特殊的引用类型且是`final`的，JVM使用字符串常量池存储字符串数据。创建新的字符串，JVM会先去查找常量池中是否有该字符串，如果有，直接返回该字符串在常量池中的引用，如果没有，则添加到常量池。
2. `String s = "a"; s += "b";`，这段代码执行前后，字符串常量池中将出现a和ab两个字符串常量，而原本s变量的引用指向了常量池中ab。
3. `String s = new String("ab")`，这段代码一共创建了几个对象？一个或两个。如果字符串常量池中有了`ab`这个字符串(比如在此之前已经使用了`String str = "ab"`)，那么新的s对象引用其实仅仅是指向了字符串常量中的ab，并没有创建新的字符串对象。但是，每次调用`new`都会在堆内存开辟空间，创建一个String对象，这是肯定的。

### String和StringBuffer和StringBuilder关系
1. String是不可变字符串，StringBuilder和StringBuffer是可变字符串，如果经常改变字符串的原始数据，最好使用StringBuffer代替。
2. StringBuffer是线程安全的，效率低，StringBuffer是非线程安全的，效率高。
3. String重写了`equals（）`方法和`hashCode（）`方法；而StringBuilder没有重写`equals（）`方法，使用`new StringBuffer("")`会直接在堆内存中开辟空间储存对象。因此将`StringBuffer`对象储存仅Java集合中可能会出现问题。

### static关键字
1. static方法只能访问static变量或方法
2. 非static标记的方法可以访问static或非static方法或变量
