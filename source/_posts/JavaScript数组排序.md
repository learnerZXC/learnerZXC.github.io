---
title: JavaScript数组排序
date: 2018-09-13 22:43:27
tags: Array
categories: JavaScript
---
# JavaScript数组排序
数组中我们经常碰到对数组进行排序处理，数组排序通常使用sort()方法进行排序，并返回数组。即会改变原来的数组。但排序不一定是稳定的，默认排序是根据字符串的Unicode编码进行排序的。

由于取决于具体实现，所以无法保证排序的时间和空间复杂性

例如：

```javascript
var months = ['march', 'Jan', 'Feb', 'Dec'];
months.sort();
console.log(months)	//["Dec", "Feb", "Jan", "march"]

var array1 = [1, 30, 4, 21]
array1.sort();
console.log(array1) // [1, 21, 30, 4]
```

可以看出来，array1的排序效果并不是按照数字的从大到小排列的，没有达到想要的效果，要想达到想要的效果，可以使用以下语法：

### 语法

```javascript
arr.sort([compareFunction])
```

#### 参数

`compareFunction` | 可选

用来指定按某种顺序进行排列的函数。如果省略，元素按照转换为的字符串的各个字符的Unicode位点进行排序

#### 返回值

排序后的数组。！！！注意，数组已原地进行排序，并且不进行复制，想要回去，不可以了。

### 描述

如果没有指明 `compareFunction` ，那么元素会按照转换为的字符串的诸个字符的Unicode位点进行排序。例如 "Banana" 会被排列到 "cherry" 之前。当数字按由小到大排序时，9 出现在 80 之前，但因为（没有指明 `compareFunction`），比较的数字会先被转换为字符串，所以在Unicode顺序上 "80" 要比 "9" 要靠前。



如果指明了 `compareFunction` ，那么数组会按照调用该函数的返回值排序。即 a 和 b 是两个将要被比较的元素

- 如果 `compareFunction(a, b)` 小于 0 ，那么 a 会被排列到 b 之前；

- 如果 `compareFunction(a, b)` 等于 0 ， a 和 b 的相对位置不变。备注： ECMAScript 标准并不保证这一行为，而且也不是所有浏览器都会遵守（例如 Mozilla 在 2003 年之前的版本）；

- 如果 `compareFunction(a, b)` 大于 0 ， b 会被排列到 a 之前。
- `compareFunction(a, b)` 必须总是对相同的输入返回相同的比较结果，否则排序的结果将是不确定的。

所以对数字进行排序时，比较函数可以简单的以a减b,如下的函数将数字升序排列

```
function compareNumbers(a, b) {
    return a - b
}
```

`sort`方法可以使用函数表达式方便的书写：

```javascript
var numbers = [4, 2, 5, 1, 3];
numbers.sort(function(a, b) {
  return a - b;
});
console.log(numbers); // [1, 2, 3, 4, 5]

也可以写成：
var numbers = [4, 2, 5, 1, 3]; 
numbers.sort((a, b) => a - b); 
console.log(numbers); // [1, 2, 3, 4, 5]
```

这样就可以达到升序效果，同理降序及比较函数写为b减a

对不能转换为数字的字符串数组进行排序时，升序可以直接调用sort()方法，降序可以先调用sort()再调用reverse()方法即可答到效果

（------未完待续------）