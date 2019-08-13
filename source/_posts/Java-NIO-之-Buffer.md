title: Java NIO 之 Buffer
author: Sion
tags:
  - Java基础
  - Java NIO
categories: []
date: 2019-08-12 14:25:00
---
### Buffer（缓冲区）介绍

Java NIO Buffers 用于和 NIO Channel 交互。我们从 Channel 中读取数据到 Buffers 里，从 Buffers 把数据写入 Channels

Buffer 本质上是一块内存区，可以用来写入数据，并在稍后读取出来。这块内存被 NIO Buffer 包裹起来，对外提供一系列的读写方便开发的接口。

<!-- more -->

### 利用 Buffer 读写数据，通常遵循四个步骤：

1. 把数据写入 buffer，buffer会记录写入数据的大小；
2. 调用 flip（）把 buffer 从写模式转为读模式；
3. 从 Buffer 中读取数据，读取完数据后，需要清空 buffer，以满足后续写入操作；
4. 调用 buffer.clear（）或 buffer.compact（），clear 是清空整个 buffer，compact 是清空已读取的数据。

