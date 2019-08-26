title: Java NIO 之 Selector
author: Sion
tags:
  - Java NIO
  - Java 基础
categories:
  - 技术
date: 2019-08-26 08:33:00
---
### Selector（选择器）介绍

**Selector**一般称为**选择器**，也可翻译为**多路复用器**，是Java NIO核心组件中的一个，用于检查一个或多个NIO Channel的状态是否处于可读、可写，如此实现单线程管理多个Channel，也就是管理多个网络连接

使用Selector的好处：可以使用更少的线程来处理通道了，避免了线程的上下文切换引起的开销

<!-- more -->