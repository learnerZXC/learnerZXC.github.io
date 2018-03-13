---
title: Java集合之Map接口
date: {{data}}
tags: Map接口
categories: Java集合
---

# Java集合之Map接口

### 简介<br/>

`public interface Map<K,V>`

Map是将键映射到值的对象。一个映射不能包含重复的键；每个键最多只能映射到一个值。
<!--more-->

### 方法及其介绍
- `clear()`:从此映射中移除所有映射关系（可选操作）。

返回值类型：无返回值

- `containsKey(Object key)`：如果此映射包含指定键的映射关系，则返回 true。

返回值类型：boolean类型

- `containsKey(Object value)`：如果此映射将一个或多个键映射到指定值，则返回 true。

返回值类型：boolean类型

- `entrySet()`:返回此映射中包含的映射关系的 Set 视图。

返回值类型：Set<Map.Entry<K,V>>

- `equals(Object o)`:比较指定的对象与此映射是否相等。

返回值类型：boolean类型

- `get(Object Key)`:返回指定键所映射的值；如果此映射不包含该键的映射关系，则返回 null。

返回值类型：V

- `hashCode()`:返回此映射的哈希码值

返回值类型：int

- `isEmpty`:如果此映射未包含键-值映射关系，则返回 true。

返回值类型：boolean

- `KeySet()`:返回此映射中包含的键的 Set 视图。

返回值类型：Set<K>

- `put(K key,V value)`: 将指定的值与此映射中的指定键关联（可选操作）。

返回值类型：V

- `putAll(Map<? extends K,? extends V> m)` 从指定映射中将所有映射关系复制到此映射中（可选操作）。

返回值类型：无返回值

- `remove(Object key)`:如果存在一个键的映射关系，则将其从此映射中移除（可选操作）。

返回值类型：V

- `size()`:返回此映射中的键-值映射关系数，如果该映射包含的元素大于 Integer.MAX_VALUE，则返回 Integer.MAX_VALUE。

返回值类型：int

- `values`:返回此映射中包含的值的 Collection 视图。

返回值类型：Collection<V>
