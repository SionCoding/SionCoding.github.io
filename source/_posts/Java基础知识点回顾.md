title: Java基础知识点回顾
author: Sion
tags:
  - JavaSE
  - ''
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