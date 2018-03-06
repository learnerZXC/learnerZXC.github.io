---
title: hashcode()和equals()方法的作用？
date: 2018-03-06 23:54:46
tags:
categories:面试题
---
hashcode()和equals()方法的作用？什么时候必须重写？

jdk中对equals()和hashcode()这两个方法的定义和规范如下：
equals(Object obj)方法来判断两个对象是否相同？如果“相同”，则返回true,否则返回false.

hashcode()方法返回一个int数，在Object中的默认实现是“将该对象的内存地址转换成一个整数返回”。
Java中任何一个对象都具有equals()和Hashcode()方法，因为他们是在Object类中定义的。

hashcode()方法的作用：HashCode的存在主要是用于查找的快捷性，HashCode是用来在散列存储结构中确定对象的存储地址的；

equals()方法的作用：equals()方法是来判断两个方法是否相同的。

关于这两个方法的重要规范：
1. 如果两个对象相同，equals()方法一定返回true,并且这两个对象的hashcode一定相同。
2. 如果两个对象的HashCode相同，不代表两个对象就相同，只能说明这两个对象在散列存储结构中，存放于同一个位置。
