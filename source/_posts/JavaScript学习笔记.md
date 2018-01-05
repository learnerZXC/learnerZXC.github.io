---
title: JavaScript学习笔记
date: {{data}}
tags: JavaScript
categories:
---

### JavaScript学习笔记
#### 什么是JavaScript?
JavaScript一种直译式脚本语言，是一种动态类型、弱类型、基于原型的语言，内置支持类型。它的解释器被称为JavaScript引擎，为浏览器的一部分，广泛用于客户端的脚本语言，最早是在HTML（标准通用标记语言下的一个应用）网页上使用，用来给HTML网页增加动态功能。

完整的JavaScript由ECMAScript(语法)、Brower Object(DOM、BOM)（特性）组成的。
#### JavaScript语法
##### 注释
`//`单行注释

`/**/`多行注释
##### 语法
ECMAScript中的一切（变量、函数名和操作符）都区分大小写。

标识符： 变量、函数、属性的名字或者函数的参数。

标识符的命名规则：
  1. 由字母、数字、下划线（ _ ）或美元符（$）组成
  2. 不能以数字开头
  3. 不能使用关键字、保留字作为标识符。
###### 变量
ECMAScript中的变量是松散类型。换句话说，每个变量仅仅是一个用于保存至的占位符而已。

松散类型：可以用来保存任何类型的数据
  1. 变量声明：变量声明要使用var操作符

 语法：var 变量名
  2. 变量赋值：

 声明的同时赋值： var 变量名 = 值
 先声明后赋值： 变量名 = 值

 说明：省略var声明的变量是全局变量
###### 数据类型
 - 简单数据类型：Undefined、Null、Boolean、Number(NaN是一个特殊的数值)、String
 - 复杂数据类型：Object
 - ES6新增了symbol数据类型

###### typeof
功能： 检测变量类型

语法： typeof&nbsp;变量或typeof(变量)

返回值类型：string类型，有可能是：string、number、boolean、object、undefined、function

###### Number类型
 - Number: 表示整数和浮点数
 - NaN: 即非数值（Not&nbsp;a&nbsp;Number）是一个特殊的数值

说明：
 1. 任何涉及NaN的操作（例如NaN/10）都会返回NaN
 2. NaN与任何值都不相等，包括NaN本身
 3. typeof(NaN类型的值)结果为number

isNaN(n)：检测n是否为“非数值”，返回值为boolean类型，参数n可以是任意类型。

说明：isNaN对接受的值，先尝试转换为数值，再检测是否为非数值。比如：var&nbsp;age="18",Number.isNaN(age)返回值为false;

数值转换:有3个函数可以把非数值转换为数值：
 - Number()
 - parseInt()
 - ParseFloat()

 说明：
  1. Number()可以用于认可数据类型。
  2. parseInt()和parseFloat（）则专门用于把字符串转换为数值。
提取的字符串必须以数字开头，如果以非数字开头，则类型为NaN。
###### String类型
String类型用于表示由零或多个16位Unicode字符组成的字符序列，即字符串。字符串可以由双引号（""）或单引号（''）表示

数值转换： 将其他类型转换为字符串有两种方法：
 - toString()

    语法：str.toString;&nbsp;&nbsp;功能：将str转换为字符串&nbsp;&nbsp;返回值：str的一个副本<br>
    参数：str是要转换的类型，可以是数值、布尔型、对象和字符串。<br>
  - String()

  说明：在不知道要转换的值是不是Null或者undefined的情况下，还可以使用String()函数，它能够将任何类型的值转换为字符串。
###### Boolean类型
用于表示真假的类型，即true表示真，false表示假

数值转换：
 - Boolean()

 注意：
  1. 除0之外的所有数字，转换为布尔型都为true
  2. 除""之外的所有字符，转换为布尔型都为true(""是空，空格也为true)
  3. null 和 undefined转换为布尔型为false

###### 操作符
  1. 算数操作符（`+、-、*、/、% 、a++ 、++a、a--、--a`）<br>
  运算时会做隐士数据类型转换
  2. 逻辑操作符
  `&&、||、!`<br>
  &&(与):在有一个操作数不是布尔值的情况，逻辑与操作就不一定返回布尔值，此时他遵循以下规则：
    1. 如果操作数隐士类型转换后都为true,则返回最后一个操作数。例如：80&&55返回结果为55(80隐士类型转换为true).
    2. 如果操作数隐士类型转换后不都为true,则返回第一个为false的值。例如：0&55返回结果为0(0隐士转换为false).
    3. 只要有一个操作数是null，则返回null
    4. 只要有一个操作数是NaN，则返回NaN
    5. 只要有一个操作数是undefined，则返回undefined

  ||(或)：在有一个操作数不是布尔值的情况，逻辑与操作就不一定返回布尔值，此时他遵循以下规则：
    1. 如果操作数隐士类型转换后不都为false,返回第一个为true操作数。例如：80&&55返回结果为80(80隐士类型转换为true).
    2. 如果操作数隐士类型转换后都为false,则返回最后一个操作数。例如：0&55返回结果为55(0隐士转换为false).
    3. 如果两个操作数都是null，则返回null
    4. 如果两个操作数都是NaN，则返回NaN
    5. 如果两个操作数都是undefined，则返回undefined

  !(非)：
    1. 无论操作数是什么数据类型，逻辑非都会返回一个布尔值。
    2. !!同时使用两个逻辑非操作符时：
      - 第一个逻辑非操作会基于无论什么操作数返回一个布尔值
      - 第二个逻辑非则对该布尔值求反
  3. 赋值操作符<br>
  简单赋值：`=`<br>
  复合赋值：`+=、-=、*=、/=、%=`
  4. 比较操作符<br>
  `>、<、>=、<=、==、===、!=、!==`返回值为boolean类型
  5. 三元操作符<br>
  语法：条件?执行代码1:执行代码2<br/>
  说明：可替代简单if语句，如果条件成立，执行代码1，否则执行代码2
##### JavaScript条件语句
###### 分支语句
if语句<br>
switch语句
###### 循环语句
for循环<br>
语法：for(语句1;语句2;语句3){被执行的代码块}<br/>
语句1：在循环(代码块)开始前执行<br/>
语句2：定义循环（代码块）的条件<br/>
语句3：在循环(代码块)已被执行之后执行<br/>
<hr/>
while循环<br/>
语法：while(条件){需要执行的代码块}
<hr/>
do-while语句<br/>
语法：do{需要执行的代码}while(条件)<br/>
说明：这种语法的循环只是要被执行一次。
<hr/>
continue:结束本次循环，继续开始下一次。<br/>
break:退出整个循环体。
##### JavaScript内置对象
###### ECMAScript中的Array
创建数组<br/>
创建数组的基本方式有两种：
1. 使用Array构造函数<br/>
语法：new&nbsp;Array()<br/>
小括号()说明：
      - 预先知道数组要保存的项目的数量
      - 向Array构造函数中传递数组应包含的项
2. 使用数组字面量表示法：由一对包含数组项的方括号[]表示，多个数组项之间用逗号隔开。

数组长度<br/>
语法:array.length<br>
功能：获取数组array的长度
返回值：number
说明：通过设置length可以从数组的末尾移除项或者向数组中添加新项

数组的栈方法：
- push()<br/>
语法：arrayObject.push(newele1,newele2,...)<br/>
功能：把它的参数顺序添加到arrayObject的尾部。<br/>
返回值：把指定值添加到数组后的新长度。
- unshift()
语法：arrayObject.unshift(newele1,newele2,...)<br/>
功能：把它的参数顺序添加到arrayObject的开头。<br/>
返回值：把指定值添加到数组后的新长度。
- pop()
语法：arrayObject.pop()<br/>
功能：删除arrayObject的最后一个元素。<br/>
返回值：被删除的那个元素
- shift()
语法：arrayObject.pop()<br/>
功能：删除arrayObject的第一个元素。<br/>
返回值：被删除的那个元素

数组的转换方法：<br/>
`join()`<br/>
语法：arrayObject(separator)<br/>
说明：separator指访问时用什么分割符。没有参数时，默认用逗号连接起来<br/>
功能:用于吧数组中所有元素放入一个字符串。<br/>
返回值：字符串<br/>

数组重排序：<br/>
`reverse（）`<br/>
语法：arrayObject.reverse()<br/>
功能：用于颠倒数组中元素的顺序。<br/>
返回值：排完序以后的数组。<br/>

`sort()`
语法：arrayObject.sort(sortby)<br/>
功能：用于对数组中元素进行排序。<br/>
返回值：排完序以后的数组。<br/>
说明：
1. 即使数组中的每一项都说数值，sort()方法比较的也是字符串。
2. sort()方法可以接受一个比较函数作为参数。
例如：数字降序。`arrayObject.sort(function(a,b){return b-a})`

数组连接：<br/>
`concat()`<br/>
语法：arrayObject.concat(arrayX,arrayX,....)<br/>
功能：用于连接两个或者多个数组。<br/>
返回值：数组。

截取数组中的元素：<br/>
语法：arrayObject.slice(start,end)<br/>
功能：从已有的数组中截取从start和end（不包含该元素）的元素，即截取从start到end-1的元素<br/>
参数：
- start(必须)规定从何处开始选取，如果是负数，从数组尾部开始算起。
- end(可选)规定从何处结束选取，是数组片段结束处的下标。<br/>

说明：
1. 如果没有指定end，切分的数组包含从start到数组结束的所有元素。
2. 如slice()方法吃参数中有一个负数，则用数组长度加上该数来确定相应的位置。<br/>

返回值：数组<br/>

其他方法：
`splice()`<br/>

删除元素语法：arrayObject.splice(index,count)<br/>
功能：删除从index处开始的零个或者多个元素。<br/>
返回值:含有被删除的元素的数组。<br/>
说明： count是要删除的项目数量，如果设置为0，则不会删除项目。如果不设置，则删除从index开始的所有值。<br/>

插入元素语法：arrayObject.splice(index,0，item1,...,itemX)<br/>
功能：在指定位置插入值<br/>
参数：
- index：起始位置
- 0：要删除的项数
- item1,..,itemX:要插入的项<br/>
返回值：空数组。<br/>

替换元素语法：arrayObject.splice(index,count，item1,...,itemX)<br/>
功能：在指定位置插入值,且同时删除任意数量的项<br/>
参数：
- index：起始位置
- count：要删除的项数
- item1,..,itemX:要插入的项<br/>
返回值：从原始数组中删除的项（如果没有删除任何项，则返回空数组）。<br/>

关于位置的两个方法：
`indexOf()`<br/>
语法：arrayObject.indexOf(searchvalue,startIndex)<br/>
功能：从数组的开头（位置0）开始向后查找<br/>
参数：
- searchvalue:必选，要查找的项
- startIndex：可选，起始位置的索引。默认为0。<br/>
返回值：number,查找项在数组中的索引值，没有找到的情况下返回-1。<br/>

`lastIndexOf()`<br/>
语法：arrayObject.lastIndexOf(searchvalue,startIndex)<br/>
功能：从数组的末尾开始向前查找<br/>
参数：
- searchvalue:必选，要查找的项
- startIndex：可选，起始位置的索引。如没有该参数，则从数组末尾开始向前查找<br/>
返回值：number,查找项在数组中的索引值，没有找到的情况下返回-1。

注：查找的项跟数组中的项比较时，会使用全等操作，即值和数据类型都必须相等

###### String
字符串常用的方法：<br/>
- `charAt()`<br/>
语法：stringObect.charAt(index)<br/>
功能：返回stringObject中的index位置的字符。<br/>
说明：ES5中可使用"方括号加字符索引"来访问字符串中特定的字符，但IE7及更早的浏览器会返回undefined。<br/>
- `charCodeAt`<br/>
语法：stringObect.charCodeAt(index)<br/>
功能：返回stringObject中的index位置字符的字符编码。<br/>
- `indexOf()`<br/>
语法：stringObjec.indexOf("o")<br/>
功能：从一个字符串中由开头向后搜索给定的子字符串，返回子字符串的位置。<br/>
返回值：数值。<br/>
说明：如果没有找到该字符串，则返回-1。<br/>
- `lastIndexOf`<br/>
语法：stringObjec.lastIndexOf("o")<br/>
功能：从一个字符串中由末尾向前搜索给定的子字符串，返回子字符串的位置。<br/>
返回值：数值。<br/>
说明：如果没有找到该字符串，则返回-1。<br/>

字符串对象的截取方法:
`slice()`<br/>
语法：stringObject.slice(start,end)
功能：截取字符串。
参数说明：
1. start:必需，指定子字符串的开始位置。
2. end:可选，表示子字符串到哪里结束，end本身不在截取的范围之内，省略时截取至字符串的末尾。
3. 如slice()方法吃参数中有一个负数，则用数组长度加上该数来确定相应的位置。<br/>

`substring()`<br/>
说明：语法及功能同slice()完全一样。<br/>
区别在于：
1. 当参数为负数时，自动将参数转换为0。
2. substring()会将较小的数作为开始位置，吧较大的数作为结束位置。<br/>

`substr()`<br/>
语法：stringObject.substr(start,len)
功能：截取字符串。
参数说明：
1. start:必需，指定子字符串的开始位置。
2. len:可选，表示截取的字符总数，省略时截取至字符串的末尾。
3. 当start为负数时，会将传入的负数与字符串的长度相加。
4. 当len为负数时，返回空字符串。<br/>

字符串分割为数组：<br/>
`split()`<br/>
语法：stringObject.split(separator)<br/>
功能：把一个字符串分割成字符串数组。<br/>
返回值：Array。<br/>
说明：separator:必需，分隔符。<br/>

替换字符串的一些字符:<br/>
`replace()`<br/>
语法：stringObject.replace(regexp/substr,replacement)<br/>
功能：在字符串中用一些字符替换另一些字符，或替换一个与正则表达式匹配的子串。<br/>
返回值：String。<br/>
说明：regexp:必需，规定子字符串或要替换的模式的RegExp对象。<br/>
replacement:必需。 一个字符串值。<br/>

字符串转换大小写：
`toUpperCase()`<br/>
语法：stringObject.toUpperCase()<br/>
功能：把字符串转换为大写。<br/>

`toLowerCase()`<br/>
语法：stringObject.toLowerCase()<br/>
功能：把字符串转换为小写。<br/>


###### Math
###### Date

#### DOM事件
###### 什么是事件
事件就是文档或浏览器窗口中发生的一些特定的交互瞬间。

###### HTML事件
概念：直接在HTML元素标签内添加事件，执行脚本。<br/>
语法：`<tag&nbsp;事件 = "执行脚本"></tag>`。<br/>
功能：在HTML元素上绑定事件。<br/>
说明：执行脚本可以是一个函数的调用。<br/>

关于this的指向：在时间触发的函数中，this是对该DOM对象的引用。
###### DOM0级事件
执行事件的步骤：<br/>
1. 通过DOM获取HTML元素
2. （获取的HTML).事件=执行脚本。<br/>

语法：ele.事件=执行脚本<br/>
功能：在DOM对象上绑定事件<br/>
说明：执行脚本可以是一个匿名函数，也可以是一个函数的调用。<br/>
在调用自定义函数时，函数后面不要加括号。如加了括号，函数可能会自动执行，而不是被触发执行<br/>
例如：`btn.onclick= clickBtn`<br/>
      `function clickBtn(){
          alert("我是按钮")
          }`  

注：不建议使用HTML事件，原因如下：<br/>
1. 多元素绑定相同事件时，效率低。
2. 不建议在HTML元素中写JavaScript代码。<br/>
###### 事件类型
鼠标事件：<br/>
  - onload:页面加载时触发(window.onload)
  - onclick:鼠标点击时触发
  - onmouseover:鼠标滑过时触发
  - onmouseout:鼠标离开时触发
  - onfoucs:获得焦点时触发
  - onblur：失去焦点时触发
  - onchange:域的内容改变时触发(一般作用于select或checkbox或radio)
  - onsubmit: 表单中的确认按钮被点击时发生(onsubmit事件不是加在按钮上，而是表单上)
  - onmousedown: 鼠标按钮在元素上按下时触发
  - onmousemove: 在鼠标指针移动时触发
  - onmouseup: 在元素上松开鼠标按钮时触发
  - onresize: 当调整浏览器窗口的大小时触发
  - onscroll：拖动滚动条滚动时触发<br/>

#### BOM事件
###### 概念
BOM（brower&nbsp;object&nbsp;model）浏览器对象模型
###### BOM对象
BOM对包括：
- window对象<br/>
window是浏览器的一个实例，在浏览器中，window对象有双重角色，它既是通过JavaScript访问浏览器窗口的一个接口，又是ECMAScript规定的Global对象（全局对象）。<br/>
var&nbsp;age=15 等价于window.age=15</br>
所有的全局变量和全局方法都被归在window对象上。<br/>

window对象的方法：<br/>
alert方法：<br/>
语法：`window.alert（"content"）`<br/>
功能： 显示带有一段消息和一个确认按钮的警告框<br/>

confirm方法：<br/>
语法：`window.confirm"message"）`<br/>
功能： 显示带有指定消息和OK及取消按钮的对话框<br/>

prompt方法：<br/>
语法：`window.prompt("text,defaultText")`<br/>
参数说明：<br/>
 text:要在对话框中显示的纯文本（而不是HTML格式的文本）<br/>
 defaultText:默认的输入文本</br>
返回值：如果用户单机提示框的取消按钮，则返回null;如果用户单击确认按钮，则返回输入字段当前显示的文本。</br>

说明：如果文本内容太长，需要换行，使用`/n`换行

open方法</br>
语法:`window.open(pageURL,name,parameters)`</br>
功能：打开一个新的浏览器窗口或查找一个已命名的窗口</br>
参数说明：</br>
pageURL:子窗口路径</br>
name: 子窗口句柄（name声明了新窗口的名称，方便后期通过name对子窗口进行引用）</br>
parameters:窗口参数（各参数用逗号分隔）<br/>

close方法</br>
语法:`window.close()`</br>
功能：关闭浏览器窗口</br>

定时器方法：<br/>
超时调用<br/>
语法：`setTimeout(code,millisec)`<br/>
功能：在指定的毫秒数后调用函数或计算表达式<br/>
参数说明：
  1. code:要调用的函数或要执行的JavaScript代码串
  2. millisec:在执行代码前需要等待的毫秒数<br/>
注：setTimeout方法返回一个ID值，通过它取消超时调用<br/>
说明：setTimeout()只执行code一次。如果要多次调用，可以让code自身在此调用setTimeout().<br/>

清除超时调用<br/>
语法：`clearTimeout(id_of_settimeout)`<br/>
功能：取消由setTimeout（）方法设置的timeout<br/>
参数说明：id_of_settimeout：由setTimeout()返回的ID值，该值标识要取消的延迟执行代码块。<br/>

间歇调用<br/>
语法：`setInterval(code,millisec)`<br/>
功能：每隔知道的时间执行一次代码
参数说明：
  1. code:要调用的函数或要执行的JavaScript代码串
  2. millisec:周期性执行或调用code之间的时间间隔，以毫秒计<br/>
  注：setInterval方法返回一个ID值，通过它取消间歇调用<br/>

间歇调用<br/>
语法：`clearInterval(id_of_setInterval)`<br/>
功能：取消由setInterval()方法设置的interval
参数说明：
id_of_setInterval：由setInterval()返回的ID值，该值标识要取消的间歇执行代码块<br/>
  注：setInterval方法返回一个ID值，通过它取消间歇调用
<hr/>
- navigator对象<br/>
常用属性：<br/>
userAgent属性<br/>
语法：`navigator.userAgent`<br/>
功能：用来失败浏览器名称、版本、引擎以及操作系统等信息的内容。<br/>
<hr/>
- screen对象<br/>
screen对象包含有关客户端显示屏幕的信息<br/>
常用属性：<br/>
availWidth属性<br/>
语法：`screen.availWidth`<br/>
功能：返回可用的屏幕宽度<br/>

availHeight属性<br/>
语法：`screen.availHeight`<br/>
功能：返回可用的屏幕高度<hr/>

- history对象<br/>
history对象保存了用户在浏览器镇南关访问页面的历史记录。是window对象的属性。<br/>

常用方法：<br/>
back()方法<br/>
语法：`history.back()`<br/>
功能：回到历史记录的上一步。<br/>
说明：相当于使用了histoyr.go(-1)。<br/>

forward()方法<br/>
语法：`history.forward()`<br/>
功能：回到历史记录的下一步。<br/>
说明：相当于使用了histoyr.go(1)。<br/>

go()方法<br/>
语法：`history.go(-n)`<br/>
功能：回到历史记录的前n步。<br/>
语法：`history.go(n)`<br/>
功能：回到历史记录的后n步。<hr/>

- location对象<br/>
location对象提供了与当前窗口加载的文档有关的信息，还提供了一些导航功能，它既是window对象的属性，也是document对象的属性。<br/>

常用属性：<br/>
href属性<br>
语法：`location.href`或`location.href='URL'`<br/>
功能：返回当前加载页面的完整URL或者跳转到设定URL（会在历史记录中生存记录）<br/>
说明：location.href与window.location.href等价<br/>

hash属性<br/>
语法：`location.hash`
功能：返回URL中的hash（#号后跟零或多个字符），如果不包含则返回空字符串。<br/>

host属性<br/>
语法：`location.host`
功能：返回服务器名称和端口号（如果有）<br/>

hostname属性<br/>
语法：`location.hostname`
功能：返回不带端口号的服务器名称。<br/>

pathname属性<br/>
语法：`location.pathname`
功能：返回URL中的目录和（或）文件名。<br/>

port属性<br/>
语法：`location.port`
功能：返回URL中指定的端口号，如果没有，返回空字符串。<br/>

protocol属性<br/>
语法：`location.protocol`
功能：返回页面使用的协议。<br/>

search属性<br/>
语法：`location.search`
功能：返回URL的查询字符串，这个字符串以?开头。<br/>

常用方法：<br/>
replace()方法<br/>
语法：`location.replace(url)`<br/>
功能：重新定向URL。<br/>
说明：使用location.replace()不会再历史记录中生成新纪录。<br/>

reload()方法：<br/>
语法：`location.reload()`<br/>
功能：重新加载当前显示的页面。
说明：
- location.reload()有可能从缓存中加载
- location.reload(true)从服务器重新加载<hr/>

- document对象
- event对象
