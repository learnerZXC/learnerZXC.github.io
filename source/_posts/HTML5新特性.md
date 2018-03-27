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

补充：

    1. header/section/aside/article/footer 最好不要互相嵌套在相同的标签里面（举例：header标签里面最好不要再嵌套个header标签）

    2. 级别：header/section/footer >aside/article/figure/hgroup/nav>div/figcapition


#### 多媒体标签

- `<video>`: 标记定义一个视频。

- `<audio>`: 标记定义音频内容。

- `<source>`: 标记定义媒体资源。

- `<canvas>`: 标记定义图片

- `<embed>`: 标记定义外部可交互的内容或插件，比如flash。

标签意义：多媒体标签的出现意味着富媒体的发展以及支持不使用插件的情况下即可操作媒体文件，极大地提升了用户体验。

#### Web应用标签

状态标签：

  - `<meter>`: 状态标签（实时状态显示：气压、气温）
  - `<progress>`: 状态标签（任务过程：安装、加载）

#### 其他标签
