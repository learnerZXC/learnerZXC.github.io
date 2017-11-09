---
title: Java多线程（三）-停止线程
date: {{data}}
tags: Java多线程
categories: Java基础
---
## 停止线程
Java中有以下3种方法可以终止正在运行的线程：

1. 使用退出标志，使线程正常退出，也就是当run方法完成后终止线程。
2. 使用stop方法强行终止线程，但不推荐使用该方法，因为stop和suspend及resume方法一样，都是作废过期的方法，使用它们可能产生不可预料的结果。
3. 使用interrupt方法终止线程。

<!--more-->

### 判断线程是否是停止状态
Thread类中提供了两种方法判断线程是否停止：

1. this.interrupted():测试当前线程是否是中断状态（当前宣布从是指运行this.interrupted()方法的线程）。执行后具有将状态标志清楚为false的功能。
2. this.isInterrupted():测试线程Thread对象是否是中断状态，但不清除状态标志。

### 如何停止线程呢
调用interrupt()方法的使用效果并不像for+break语句那样，马上就停止循环。仅仅是在当前线程中打了一个停止的标记，并不是真正的停止线程。

-  能停止线程的方法——异常法


可在线程中用for语句来判断一下线程是否是停止状态，如果是停止状态，则后面的代码不再运行即可，如果直接使用for+break，只是会停止循环，后面代码还会继续运行。如何解决语句继续运行的问题呢？在for循环中抛出异常即可。实例如下：

MyThread.java代码如下：
``` java
package exthread;
public class Mythread extends Thread{
	@override
	public void run(){
		super.run();
		try{
			for(int i = 0; i < 500000; i++){
				if(this.interrupted()){
					System.out.println("已经是停止状态了！ 我要退出了！")；
					//break;
					throw new InterruptedException();
				}
				System.out.println("i=" +(i+1))；
			}
			System.out.println("我在for下面")
		} catch(InterruptedException){
			System.out.println("进入MyThread.java类run的catch了！")；
			e.printStackTrace();
		}
	}
}
```
类Run.java代码如下：
``` java
package test;
import extherad.MyThread;
public class Run{
	public static void main(String[] args){
		try{
			MyThread thread = new MyThread();
			thread.start();
			Thread.sleep(2000);
			thread.interrupt();
		}catch(InterruptedException e){
			System.out.println("main catch");
			e.printStackTrack();
		}
	}
}
```
如果直接使用for+break语句，虽然for循环会停止；但是“我在for下面还是会输出”。如果使用抛异常方法。则for循环后面的语句也不会执行。达到停止线程效果。

- 在沉睡中停止

``` java
public class MyThread extends Thread {
	@override
	public void run (){
		super.run();
		try{
			System.out.println("run begin");
		}
	}
}

```
- 使用return停止
- 暴力停止
-
