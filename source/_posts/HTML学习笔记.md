---
title: HTML学习笔记
date: {{data}}
tags: HTML
categories:
---

## HTML学习笔记
#### HTML概念
HTML（Hypertext Markup Language）即超文本标记语言。是标准通用标记语言下的一个应用，也是一种规范，一种标准，它通过标记符号来标记要显示的网页中的各个部分。
<!--more-->
### HTML特点
- HTML不需要编译，直接由浏览器执行
- HTML是一个文本文件
- HTML 文件必须使用html或者htm为文件后缀名
- HTML对大小写不敏感。HTML和html一样
### HTML基础语法
1. HTML 基本结构
<!DOCTYPE html>    ——————声明文档类型
<html>
<head>
  网页头部信息
  <title>标题</title>
</head>
<body>  
    网页主体内容
</body>
</html>
<head></head>标签内的所有内容不会再网页中显示
2. HTML标签
 - 成对出现，开始标签和结束标签，结束标签比开始标签多了一个/
 - 单标签：没有结束标签。例如<hr/>
 1. 标题标签:<h1></h1>~<h6></h6>
 2. 段落标签：<p></p>
 3. 换行标签：<br/>
 4. 水平线标签<hr/>
 5. 文字斜体：<i></i>、<em></em>
 6. 文字加粗：<b></b>、<strong></strong>
 7. 下标：<sub></sub>   上标：<sup></sup>
 8. 插入内容（下划线）：<ins></ins> 删除内容：<del></del>
 9. 特殊符号: 比如&lt; <
 10. 无序列表：<ul><li></li></ul>
 11. 有序列表：<ol><li></li></ol>
 12. 定义列表：<dl><dt>定义列表项</dt><dd>列表项描述</dd><dd>列表项描述</dd></dl>
 13. 锚链接（同一页面）：<a href="#锚名">目录名</a>
 14. 锚链接（不同页面页面）：<a href="网页名称#锚名">目录名</a>
 15. 电子邮箱链接： <a href="mailto:邮件地址">名称</a>
3. HTML元素
4. HTML属性
5. 注释
html使用<!-- -->进行注释
