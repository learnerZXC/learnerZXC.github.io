---
title: Java多线程（二）-线程的基本方法
date: {{data}}
tags: Java多线程
categories: Java基础
---

## currentThread()方法
currentThread（）方法可返回代码段正在被哪个线程调用的信息
## isAlive()方法
isAlive()方法是判断线程是否处于活动状态。
## sleep（）方法
sleep()方法的作用是在指定的毫秒数内让当前“正在执行的线程”休眠（暂停执行）。这个“正在执行的线程”是指this.currentThread（）返回的线程。
## getId()方法
getId()方法作用是取得线程的唯一标识
## getName()方法
getName方法是取得线程的名称。
