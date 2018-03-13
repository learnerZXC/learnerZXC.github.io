---
title: Java集合之Collection接口
date: {{data}}
tags: Collection
categories: Java集合
---

# Java集合之Collection接口

### 简介

`public interface Collection<E>extends Iterable<E>`

Collection 表示一组对象，这些对象也称为 collection 的元素。一些 collection 允许有重复的元素，而另一些则不允许。一些 collection 是有序的，而另一些则是无序的。JDK不提供此接口的任何直接实现：它提供更具体的子接口（如 Set 和 List）实现。此接口通常用来传递 collection，并在需要最大普遍性的地方操作这些 collection。

### 方法及其介绍

- `add(E e)`: 确保此 collection 包含指定的元素（可选操作）。如果此 collection 由于调用而发生更改，则返回 true。（如果此 collection 不允许有重复元素，并且已经包含了指定的元素，则返回 false。）

返回： boolean类型

- `remove(Object o)`: 从此 collection 中移除指定元素的单个实例，如果存在的话（可选操作）。更确切地讲，如果此 collection 包含一个或多个满足 (o==null ? e==null : o.equals(e)) 的元素 e，则移除这样的元素。如果此 collection 包含指定的元素（或者此 collection 由于调用而发生更改），则返回 true 。

返回：boolean类型

- `size()`: 返回此 collection 中的元素数。如果此 collection 包含的元素大于 Integer.MAX_VALUE，则返回 Integer.MAX_VALUE。

返回：int类型

- `isEmpty()`: 如果此 collection 不包含元素，则返回 true。

返回：boolean类型

- `contains(Object o)`: 如果此 collection 包含指定的元素，则返回 true。更确切地讲，当且仅当此 collection 至少包含一个满足 (o==null ? e==null : o.equals(e)) 的元素 e 时，返回 true。

返回： boolean类型

- `iterator()`: 返回在此 collection 的元素上进行迭代的迭代器。关于元素返回的顺序没有任何保证（除非此 collection 是某个能提供保证顺序的类实例）。

返回： Iterator<E>

- `toArray()`: 返回包含此 collection 中所有元素的数组。

返回： 包含此 collection 中所有元素的数组。

- `constainsAll()`: 如果此 collection 包含指定 collection 中的所有元素，则返回 true。

返回：boolean类型

- `addAll(Collection<? extends E> c)`:将指定 collection 中的所有元素都添加到此 collection 中（可选操作）。如果在进行此操作的同时修改指定的 collection，那么此操作行为是不确定的。（这意味着如果指定的 collection 是此 collection，并且此 collection 为非空，那么此调用的行为是不确定的。）

返回： 如果此 collection 由于调用而发生更改，则返回 true

- `removeAll(Collection<?> c)`: 移除此 collection 中那些也包含在指定 collection 中的所有元素（可选操作）。此调用返回后，collection 中将不包含任何与指定 collection 相同的元素。

返回： 如果此 collection 由于调用而发生更改，则返回 true

- `retainAll(Collection<?> c)`: 仅保留此 collection 中那些也包含在指定 collection 的元素（可选操作）。换句话说，移除此 collection 中未包含在指定 collection 中的所有元素。

返回： 如果此 collection 由于调用而发生更改，则返回 true

- `clear()`: 移除此 collection 中的所有元素（可选操作）。此方法返回后，除非抛出一个异常。

返回： 无返回值。

- `equals(Object o)`: 比较此 collection 与指定对象是否相等。

返回：如果指定对象与此 collection 相等，则返回 true

- `hashCode()`：返回此 collection 的哈希码值。

返回：此 collection 的哈希码值（int类型）
