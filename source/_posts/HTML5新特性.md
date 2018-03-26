---
title: HTML5新特性
date: 2018-03-26 22:44:34
tags: HTML 5
categories: HTML
---
# HTML5学习笔记

## HTML5标签变化

### HTML <!DOCTYPE> 标签

<!DOCTYPE> 声明必须是HTML的第一行，位于<html>标签之前。

<!DOCTYPE>不是HTML标签，而是只是浏览器关于页面使用哪个HTML版本进行编写的指令。

常用的DOCTYPE声明：
  - HTML 4.01 Strict:该 DTD 包含所有 HTML 元素和属性，但不包括展示性的和弃用的元素（比如 font）。不允许框架集（Framesets）。

  `<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">`

  - HTML  4.01 Transitional: 该 DTD 包含所有 HTML 元素和属性，包括展示性的和弃用的元素（比如 font）。不允许框架集（Framesets）。

  `<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
  "http://www.w3.org/TR/html4/loose.dtd">`

  - HTML 4.01 Frameset:该 DTD 等同于 HTML 4.01 Transitional，但允许框架集内容。
    `<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN"
    "http://www.w3.org/TR/html4/frameset.dtd">`

  - HTML5
  `<!DOCTYPE html>`

注：在 HTML 4.01 中，<!DOCTYPE> 声明引用 DTD，因为 HTML 4.01 基于 SGML。DTD 规定了标记语言的规则，这样浏览器才能正确地呈现内容。HTML5 不基于 SGML，所以不需要引用 DTD。

提示：请始终向 HTML 文档添加 <!DOCTYPE> 声明，这样浏览器才能获知文档类型。

### 新增的标签

#### 结构标签
结构标签（块状元素）：可以认为是个有意义的div.

- `<article>` : 标记定义一篇文章

- `<header>`: 标记定义一个页面或一个区域的头部

- `<nav>`: 标记定义导航链接

- `<section>`: 标记定义一个区域

- `<aside>`: 标记定义页面内容部分的侧边栏

- `<hgroup>`: 标记定义文件中一个区块的相关信息

- `<figure>`: 标记定义一组媒体内容以及它们的标题

- `<figcaption>`: 标记定义figure元素的标题

- `<footer>`: 标记定义一个页面或一个区域的底部

- `<dialog>`： 标记定义一个对话框（会话框）类似微信


#### 多媒体标签

#### Web应用标签

#### 其他标签
