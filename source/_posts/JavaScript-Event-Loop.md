---
title: JavaScript Event Loop
date: 2019-04-07 21:41:37
tags: {{data}}
categories: javaScript
---

# JavaScript EventLoop(事件循环)

## 前言

​	JavaScript从诞生之日就是一门单线程的非阻塞的脚步语言。这是由最初的用途来决定的：与浏览器交互。

​	单线程以为着，JavaScript代码在执行的任何时候，都只有一个主线程来处理所以任务。

​	而非阻塞则当代码需要进行一项异步任务(无法立刻返回结果，需要花一定时间才能返回事物，如 I/O事件)的时候，主线程会挂起(pending)这个任务，然后异步任务返回结果的时候根据一定的规则进行相应的回调。而非阻塞证书通过 Event Loop(事件循环实现的)

## 堆、栈、队列

### 栈(LIFO，先进后出，后进先出)

​	栈是一种遵循后进先出原则的有序集合。新添加的或者待删除的元素都保存着栈的末尾。栈内存一般存储基本数据类型(Number、String、Null、Undefined、Boolean以及es6新引入的 Symbol)。我们可以直接操作保存在栈内存空间的值，因此基本数据类型都是按值访问。

​	函数调用星神了一个栈帧。

```js
	function foo(b) {
    var a = 10;
    return a + b + 11;
  }

  function bar(x) {
    var y = 3;
    return foo(x * y);
  }

  console.log(bar(7)); // 返回 42
```

​	当调用bar 时，创建了第一帧，帧中包含了bar的参数和局部变量。当bar调用foo时，第二个帧就被创建，并压在第一个帧之上，帧中包含了foo的参数和局部变量。当foo返回时，最上层的帧就被弹出栈(剩下 bar函数的调用帧)。当 bar 返回时栈就空了。



### 堆

​	对象被分配在一个堆中，即用以表示一大块非结构的得内存区域。 js的引用类型，比如数组Array,Object他们值的大小不固定，通常被保存着堆内存中。JS不允许之家操作保存在栈内存空间的值，因此我们在操作对象时，事件上是在操作对象的引用而不是实际对象本身。所以我们复制这个变量只是复制了引用地址，而不是复制了这个对象。我们可以理解为我们操作的是保存在堆内存中的一个地址，该地址与堆内存的实际值相关联。



### 队列(FIFO，先进先出)

​	队列和栈不同的是，队列遵循FIFO，也就是先进新出的原则。队列从尾部添加新元素，从底部移除新元素，最新添加的元素必须拍了在队列的末尾。

​	一个JavaScript运行时包含了一个待处理的消息队列。每一个消息都关联着一个用以处理这个消息的函数。

​	在时间循环期间的某个时刻，运行从最先进入队列的消息开始处理队列中的消息，为此，这个消息会被移除队列，并作为输入参数调用与之关联的函数。正如前面所提到，调用一个函数总是会为其创造一个新的栈帧。

​	函数的处理会一直进行到执行栈再次为空为止；然后时间循环将会处理队列中的下一个消息。

## Event Loop(事件循环)

​	任务队列中所以任务都是乖乖排队的吗？答案是否定的，任务也是有区别的，总有任务会有一些特权——微任务(micro-task)，也有些任务没有特权，只能乖乖排队——宏任务(masro-task)。

​	通常任务宏任务包括以下任务：

* setTimeout

* setinterval

* setImmediate

* I/O

​	微任务包含以下任务源

 * process.nextTick
 * Promise
 * Object.observe
 * MutationObserver

参考： 

​	https://juejin.im/post/5aab2d896fb9a028b86dc2fd

​	https://zhuanlan.zhihu.com/p/33058983

​	https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/EventLoop