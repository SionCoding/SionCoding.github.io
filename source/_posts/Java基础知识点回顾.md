title: Java基础知识点回顾
author: Sion
tags:
  - JavaSE
categories:
  - 技术
date: 2019-07-16 10:03:00
---
### Java基础

#### JDK和JRE区别
1. `jre`即Java Runtime Environment，Java运行环境。包括Java虚拟机和Java类库
2. `jdk`是Java开发工具包，例如：`tools.jar`

<!-- more -->

#### == 和 equals 区别
1. `==`是一个比较运算符，对于基本类型，比较的是具体的数值(int、double..)；对于引用类型，比较的是对象的内存地址
2. `equals`是超类`Object`就具有的方法，因此所有的引用类型都具有这个方法，只用用来比较引用数据类型。`equals`方法默认比较的对象内存地址，如果重写该方法，一般比较的是对象的属性值

#### final的作用
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

#### String属于基本类型吗
##### 不，String属于特殊的引用类型

Java中属于基本类型的有：int、short、long、char、boolean、float、double、byte
1. `String`是特殊的引用类型且是`final`的，JVM使用字符串常量池存储字符串数据。创建新的字符串，JVM会先去查找常量池中是否有该字符串，如果有，直接返回该字符串在常量池中的引用，如果没有，则添加到常量池。
2. `String s = "a"; s += "b";`，这段代码执行前后，字符串常量池中将出现a和ab两个字符串常量，而原本s变量的引用指向了常量池中ab。


















