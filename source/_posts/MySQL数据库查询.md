---
title: MySQL数据库查询
date: 2017-11-06 22:47:25
tags: MySQL数据库
categories: 数据库
---
### MySQL查询的5种子句：
where(条件查询)、having(筛选)、group by(分组)、order by(排序)、limit(限制结果数)

### 连接查询
连接查询：将多张表(>=2)进行记录的连接(按照某个指定的条件进行数据拼接)。
连接查询的意义: 在用户查看数据的时候,需要显示的数据来自多张表.
- 内连接（inner join）

INNER JOIN定义：在查询的几个表中，每个表都存在至少一个匹配时，INNER JOIN 关键字返回行。也就是共有部分，即几个表的交集。

```
SELECT * FROM table1 INNER JOIN table2 ON 查询条件;
```
- 外连接（outer jion）
  - 左外连接(left outer jion)

  LEFT JOIN定义：关键字会从左表那里返回所有的行，即使在右表 中没有匹配的行，右表没有的都会显示NULL。
  ```
  SELECT * FROM table1(左表) LEFT JOIN table2(右表) ON 查询条件;
  ```
  - 右外连接(right outer jion)

  RIGHT JOIN定义：关键字会右表那里返回所有的行，即使在左表中没有匹配的行，左表没有的都会显示NULL。
  ```
  SELECT * FROM table1(左表) RIGHT JOIN table2(右表) ON 查询条件;
  ```
  - 完全外连接(full join)

  是结合左连接与右连接的方式，会得到两表都会没有的记录，以NULL的形式显示，但是MySQL不支持。不过可以用UNION关键字来建立左连接与右连接
  ```
  SELECT * FROM table1(左表) LEFT JOIN table2(右表) ON 查询条件（注意不要有分号）
  UNION
  SELECT * FROM table1(左表) RIGHT JOIN table2(右表) ON 查询条件;
  ```
- 自然连接(natural jion)

自然连接的作用：自动将表中相同的列进行匹配，同时排除掉重复出现的列，保证相同的列只出现一次。
```
SELECT * FROM table1 natural join table2;
```

### 子查询
子查询是一个查询语句嵌套着另外的查询语句，用来进行一定层次的查询，其中子查询相当于第一步查询过滤，外查询就是最后得到结果的查询。

### 合并查询
合并查询主要是UNION与UNION ALL两个，是将查询结果合并，但是必须满足：合并的列的数据与数据类型必须相同。
