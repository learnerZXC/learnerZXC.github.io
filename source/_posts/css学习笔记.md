---
title: CSS学习笔记
date: {{data}}
tags: CSS
categories:
---

## CSS学习笔记
### 什么是CSS？
CSS 层叠样式表（Cascading Style Sheets）
- 用于定义HTML内容在浏览器内的显示样式
<!--more-->
### CSS学习
#### HTML页面的三种布局方式：
  - 标准流
  - 浮动
  - 定位
#### css基础语法
css 规则有两部分构成：选择器，声明
#### css注释
/*注释内容*/
#### css使用方法
- 行内样式（内联样式）：同时加载

例如：<p Style="color: red;">内容</p>
- 内部样式表（嵌入样式）：同时加载

 CSS样式<style type="text/css">样式</style>

注：<style></style>要放在<head>标签之间

-内部样式表（导入式）：在读取完html文件之后加载

例如：<style  type="text/css">
        @import url(css的url地址)；或者@import"css的url地址"
      </style>
- 外部样式表： 页面加载时，同时加载CSS样式

1. 外部样式表，把CSS样式代码写在独立的一个文件中，名称：文件名.css
2. 引入外部文件<link href="XX.css" rel="stylesheet" type="text/css"/>

注：<link/>标签要放在<head>标签之间

#### css选择器
css选择器有以下类型：
- 标签选择器

以html标签作为选择器。 例如：h1{font-size: 30px;}
- 类选择器

为HTML标签添加class属性，通过类选择器来为具有此class属性的元素设置css样式
例如：<h1 class="classname">内容</h1>     .classname{color:red;}
还可以对不同类型元素的同一名称的类选择器设置不同的样式规则
例如<h1 class="red">内容<h1> <p class="red">内容</p>
p.red{font-size:50px;} h1.red{font-size:20px}
- ID选择器

为HTML标签添加ID属性，通过ID选择器来为具有此ID属性的元素设置css样式
<p id="one">内容</p>   #one{color:green;}
- 全局选择器

所有标签设置样式 例如：`*{color: blue;}`

- 群组选择器

集体统一设置样式 例如：p,h1,h2,h3{font-size:50px;}
- 后代选择器

使用后代选择器设置，之间用空格隔开
例如：<p><em>css</em>层叠样式</p>  p em{font-size:40px;}
- 伪类

伪类选择器定义特殊状态下的样式，无法用标签、id、class及其他属性实现
例如：链接伪类 <a href=""></a>

a:link{color:blue;} --为访问的链接  a:visited{color:red;} --已访问的链接
a:hover{color:green;} --鼠标悬停状态 a:active{color:gray;} --激活的链接
链接伪类的顺序： :link>:visited>:hover>:avtive

说明：
  1. a:hover必须置于a:link和a:visited之后，才有效
  2. a:active必须置于a:hover之后才有效
  3. 伪类名称对大小写不敏感
#### css优先级
行内样式>>内部样式>>外部样式  内部样式跟外部样式的优先级取决于接近元素的位置，越接近于元素，优先级越高

id选择器>class选择器>标签选择器

同一个元素引用多个class定义的样式，越接近于元素，优先级越高

后代选择其中，采用权值高的样式，权值相同，则采用就近原则

通过在样式中添加{!important}来调解优先级
#### css继承和层叠
css继承：从父元素继承部分属性，当上级样式与元素本身样式冲突时，会忽略继承来的样式

css层叠：
 - 可以定义多个样式
 - 不冲突时，多个样式可以层叠为一个
 - 冲突时，按不同样式规则优先级来应用样式
#### css命名规范
- 采用英文字母、数字以及"-"和`_`命名
- 以小写字母开头，不能以数字和"-"、`_`开头
- 命名形式：单字、连字符、下划线和驼峰
- 使用有意义的命名
#### css字体样式
css中字体加粗用font-weight

设置字体样式： font-style

设置元素中文本为小型大写字母： font-variant
#### css文本样式
设置段落对齐方式：` text-align`只对块级的元素起作用

设置元素内容的垂直方式： vertical-align属性。 只对行内元素、单元格元素生效，对块级元素不生效。

多行元素垂直居中，将元素转换为单元格元素`display:table-cell;`
并在其负累样式中添加`display:table`

设置元素中文本行高： `line-height:长度值|百分比`

设置字体属性： `word-spacing`设置元素内单词之间的间距(间距判断以空格为准）
              `letter-spacing`设置元素内字母之间的间距
              `text-transform`设置元素内字母的大小写
              `text-decoration`设置文本的装饰样式（下划线等等）

#### css背景和列表
##### 背景样式：
- background-color(设置元素的背景颜色)
`background-color:颜色|transparent`

说明：
 1. transparent是全透明黑色的（black）速记法，类似于rgba(0,0,0,0)这样的值。
 2. 颜色值（颜色名|RGB|十六进制）
 3. 背景去包括内容、内边距（padding）和边框，不包括外边距（margin）。边框颜色默认为文本颜色
- background-image(把图像设置为背景)

`background-image:url(url地址)|none`

说明：
 1. url地址可以是相对地址也可以是觉得地址
 2. 元素的背景占据了元素的觉得尺寸，包括内边距和边框，但不包括外边距
 3. 默认地，背景图元素位于元素的左上角，并在水平和垂直方向上重复
 4. 同时设置了背景图片和背景颜色，背景颜色会被覆盖

- background-position(设置背景图像的起始位置,,针对整个网页的位置)
`background-position:百分比|值|top|right|bottom|left|center`

- background-attachment(背景图像是否固定或者随着页面的其余部分滚动)
`background-attachment:scroll|fixed`设置元素背景图片的显示方式

说明：
 1. 默认值，背景图片岁滚动条滚动
 2. 当页面其余部分滚动是，背景图片不会移动

- background-repeat(设置背景图像是否重复及如何重复)
 1. `background-repeat: repeat`重复
 2. `background-repeat: no-repeat`不重复
 3. `background-repeat: repeat-x`水平重复
 4. `background-repeat: repeat-y`垂直重复

- background(简写属性，作用是将背景属性设置在一个声明中)
`background: [background-color] [background-image] ....`
例如：`background: #000000 url() repeat`

说明： 各值之间用空格分开，不分先后顺序
##### 列表样式
- list-style-type 设置列表项标志的类型
`list-style-type:关键字|none`

- list-style-image 将图像设置为列表标志

`list-style-type:url(图片地址)|none`

- list-style-position 设置列表中列表项标志的位置

`list-style-position:inside|outside`

说明：
 1. inside:列表项目标记放置在文本以内，且环绕文本跟据标记对齐
 2. outside: 默认值，列表项项目标记放置在文本以外，且环绕文本不根据标记对齐
- list-style 简写属性。用于吧所有列表的属性设置于一个声明中

`list-style:列表样式属性关键字`

说明：
 1. 值之间用空格隔开
 2. 顺序不固定
 3. list-style-image会覆盖list-style-type的设置
#### 盒子模型
##### 概念
  - 盒子模型用来“放”网页中的各种元素
  - 盒子设计中内容，如文字、图片等元素，都可是盒子（DIV嵌套）

##### 属性
盒子在页面中所占的宽度由左边距（左外边距）+左边框+左填充（左内边距）+内容宽度+右填充+右边框+右边距组成。高度计算同上

###### 宽度属性（内容，不含边距）
  - 宽度：`width:长度值|百分比|auto`
  - 最大宽度：`max-width:长度值|百分比|auto`
  - 最小宽度：`min-width:长度值|百分比|auto`
  设置的宽度小于最小宽度是，显示最小宽度；大于最大宽度，显示最大宽度值；值在最大宽度和最小宽度之间，显示设置值
###### 高度属性（内容，不含边距）
  - 高度：`height:长度值|百分比|auto`
  - 最大高度：`max-height:长度值|百分比|auto`
  - 最小高度：`min-height:长度值|百分比|auto`
###### 宽度和高度属性哪些可以设置
 1. 块级元素：<p>、<div>、<h1>~<h6>、<ul>、<li>、<ol>、<dl>、<dt>、<dd>等
 2. 替换元素：浏览器根据其标签的元素和属性来判断显示的具体内容<img>、<input>、<textarea>等

 ###### 边框属性
  - 边框宽度（border-width）
  设置元素边框宽度`border-width:thin|medium|thick长度值`
  - 边框颜色（border-color）
  设置元素边框颜色`border-color:颜色|transparent(透明色)`
  - 边框样式（border-style）
  设置边框样式`border-style:值`

  border-style默认值为none，设置了border-style的值宽度和颜色才能显示出来

  设置不同方向的边框属性：
  `border-top：宽度|样式|颜色`
  `border-left：宽度|样式|颜色`
  `border-bottom：宽度|样式|颜色`
  `border-right：宽度|样式|颜色`
###### 内边距（padding）属性
设置元素内容与边框之间的距离（内边距或填充），分四个方向（上右下左）
 - `padding-top:长度值|百分比`
 - `padding-right:长度值|百分比`
 - `padding-bottom:长度值|百分比`
 - `padding-left:长度值|百分比`

 说明：值不能为负值

 内边距属性缩写：
 - padding: 值1； //4个方向都为值1
 - padding: 值1 值2； //上下=值1，左右=值2
 - padding: 值1 值2 值3； //上=值1，左右= 值2，下=值3
 - padding: 值1 值2 值3 值4； //上=值1，右=值2，下=值3，左=值4
###### 外边距（margin）属性
设置元素内容与元素之间的距离（外边距或填充），分四个方向（上右下左）
 - `padding-top:长度值|百分比`
 - `padding-right:长度值|百分比`
 - `padding-bottom:长度值|百分比`
 - `padding-left:长度值|百分比`

 说明：值可以为负值

 外边距属性缩写：
 - margin: 值1； //4个方向都为值1
 - margin: 值1 值2； //上下=值1，左右=值2
 - margin: 值1 值2 值3； //上=值1，左右= 值2，下=值3
 - margin: 值1 值2 值3 值4； //上=值1，右=值2，下=值3，左=值4

 注意：

 - 默认情况下，相应HTML块级元素存在外边距，如：body、h1~h6、p等
 - 声明margin属性，覆盖默认样式。如body,h1,p{margin:0;}
 - margin值为auto,实现水平方向居中显示，由浏览器计算外边距
 - 如果垂直方向相邻的两个元素都设置margin值，去值大的
##### HTML元素分类
  - 块级元素，独占一行：<p>、<div>、<h1>~<h6>、<ul>、<li>、<ol>、<dl>、<dt>、<dd>等
  - 行内元素（内联元素），一行显示：<span>、<a>、<em>等
###### display属性
   - inline : 元素将显示为内联元素，元素前后没有换行符
   - bLock : 元素将显示为块级元素，元素前后带有换行符
   - inline-block:行内块元素，元素呈现为inline，具有block特性
   - none:此元素不会被显示

   注:
    1. 相应内联元素及使用`display:inline`设置成内联元素的width和height属性无效。水平方向`margin-left/margin-right/padding-left/padding-right`有效。垂直方向`margin-top/margin-bottom/padding-top/padding-bottom`无效
    2. 块级元素使用`display:block`设置成块级元素的width/height/margin/padding属性都生效
##### 浮动（float）属性
float中的四个参数：
  - float:left  //左浮动
  - float:right //右浮动
  - float:none  //不浮动
  - float:inherit  //继承浮动

浮动的副作用：给元素设置了浮动属性，元素可能脱离正常的标准流布局

解决副作用的方法：
  1. 手动给父元素添加高度
  2. 通过clear清除内部和外部浮动
  3. 给父元素添加overfloat属性并结合zoom:1使用
  4. 给父元素添加浮动
###### clear属性
  - clear:none
  - clear:left //不允许左边有浮动对象
  - clear:right  //不允许右边有浮动对象
  - clear:both  //不允许有浮动对象

##### 定位（position）属性
###### 意义
 - position属性决定了元素将如何定位
 - 通过top、right、bottom、left实现位置
###### position中的可选参数
 - static //默认属性，元素按照标准流排布
 - relative //相对定位，正常按照标准流排布，但可通过top、right、bottom、left改变元素位置
 - absolute //绝对定位，元素脱离正常标准流排布，通过top、right、bottom、left改变元素位置
 - fixed  //固定定位。通过top、right、bottom、left改变元素位置，不受制于父元素
 - inherit //继承父类元素的属性
###### z-index
  - 可以设置元素的叠加顺序，但依赖定位属性
  - z-index大的元素会覆盖z-index小的元素
  - z-index为auto的元素不参与层级比较
  - z-index为负值，元素会被普通流中的元素覆盖
##### css页面布局
###### 经典的行布局
 - 基础的行布局
 - 行布局自适应
 - 行布局自适应限制最大宽
 - 行布局垂直水平剧中
