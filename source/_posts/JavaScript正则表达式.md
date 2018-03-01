---
title: JavaScript正则表达式
date: {{data}}
tags: 正则表达式
categories: JavaScript
---

## JavaScript正则表达式
### 概念
正则表达式（Regular Expression）使用单个字符串来描述、匹配一系列符合某个句法规则的字符串。简单来讲就是按照某种规则去匹配符合条件的字符串。<br/>
<!--more-->
### JavaScript正则表达式语法
#### RegExp修饰符
- `g`:全文搜索
- `i`:忽略大小写
- `m`:多行搜索<br/>
ES6中新增修饰符：
- `y`:全局匹配，和g修饰符一样可以被执行多次，lastIndex移动到匹配位置的下一个位置。
不同的地方在于y修饰符必须在开始的位置匹配，g修饰符只要在剩余的部分有匹配就可以。
例如：<br/>
` let s = 'bbbb_bbb_bb_b';`<br/>
`var a1 = /b+/g;`<br/>
`var a2 = /b+/y;`<br/>
`console.log(a1.exec(s), a2.exec(s)); // ["bbbb"],["bbbb"]`<br/>
`console.log(a1.exec(s), a2.exec(s)); // ["bbb"],null`<br/>
`  console.log(a1.sticky, a2.sticky); //false,true表示是否开启了粘连模式`<br/>
ES6新增RegExp.sticky属性来判断是否开启粘连模式（y属性）,如上面所示<br/>
- `u`:Unicode模式。用来正确处理大于0xFFFF的Unicode字符。<br/>
例如：<br/>
`console.log(/\u{61}/.test('a')); // false`<br/>
`console.log(/\u{61}/u.test('a')); // true识别Unicode编码`<br/>
` console.log('u修饰符',/^\uD83D/.test('\uD83D\uDC2A')); // true`<br/>
`console.log('u修饰符',/^\uD83D/u.test('\uD83D\uDC2A')); // false`<br/>
上面代码中，\uD83D\uDC2A 是一个四字节的UTF-16 编码，代表一个字符，但是，ES5不支持四个字节的 UTF-16 编码，会将其识别为两个字符，导致第一行代码结果为 true ，加了u修饰符以后，ES6就会识别其为一个字符，所以第二行代码结果为false。<br/>
注：点（.）字符不能识别码点大于0xFFFF的Unicode字符，必须加上u修饰符。使用u修饰符后，所有量词都会正确识别大于码点大于0xFFFF的Unicode字符。<br/>
例如：<br/>
`console.log(/\u{20BB7});//𠮷`<br/>
`let s = '𠮷';`<br/>
`console.log('大于0xFFFF的Unicode字符',/^.$/.test(s)); // false`<br/>
    `console.log('使用u字符',/^.$/u.test(s)); // true`<br/>
`console.log('量词',/a{2}/.test('aa')); // true`<br/>
`console.log('量词',/a{2}/u.test('aa')); // true`<br/>
`console.log('量词',/𠮷{2}/.test('𠮷𠮷')); // false`<br/>
`console.log('量词',/𠮷{2}/u.test('𠮷𠮷')); // true`<br/>
- `s`只是提案，并不支持




#### RegExp对象
JavaScript通过内置对象RegExp支持正则表达式<br/>
有两种方式实例化RegExp对象：<br/>
- 字面量<br/>
`var reg = /\bis\b/g`(\b单词边界)<br/> //第一个参数是正则表达式，不接受第二个参数，否则会报错
`'He is a body. This is a dog. Where is she?'.replace(reg,'IS')`<br/>
`结果为"He IS a body. This IS a dog. Where IS she?"`<br/>
- 构造函数<br/>
`var reg = new RegExp('\\bis\\b','g')`//第一个参数是字符串，第二个是修饰符<br/>
`'He is a body. This is a dog. Where is she?'.replace(reg,'IS')`<br/>
`结果为"He IS a body. This IS a dog. Where IS she?"`<br/>
ES6中新增了一种写法：<br/>
`let regexp = new RegExp(/xyz/ig,'i')`//原有正则对象的修饰符是ig，它会被第二个参数i覆盖
同时新增：`RegExp.flags`获取正则对象修饰符的属性

#### JavaScript正则表达式元字符
正则表达式由两种基本字符类型组成：
- 原义文本字符<br/>
代表单词原本意义的字符<br/>
- 元字符<br/>
元字符是在正则表达式中有特殊含义的非字母字符。<br/>
注：元字符的含义并不是唯一的，在不同的环境下有不同的含义。<br/>
`* + ? $ ^ . | \ () {} []`（这些元字符的意义见下面详解）<br/>
`\t: 水平制表符`<br/>
`\v: 垂直制表符`<br/>
`\n: 换行符`<br/>
`\r: 回车符`<br/>
`\0: 空字符`<br/>
`\f: 换页符`<br/>
`\cX: 与X对应的控制字符(Ctrl + X)`<br/>

### 字符类
一般情况下正则表达式一个字符对应字符串一个字符<br/>
我们可以使用元字符[]来构建一个简单的类，所谓类是指符合某些特性的对象，一个泛指，而不是特指某个字符。<br/>
例：表达式`[abc]`把字符a或b或c归为一类，表达式可以匹配这类字符。是指属于a或b或c中的一个即为匹配。<br/>
#### 字符类取反
使用元字符^创建反向类/负向类，便是不属于某类的类容
例：[^abc]指不属于字符a或b或c的内容

### 范围类
- 我们可以使用[a-z]来连接两个字符表示从a到z的任意字符
注：这是闭区间，也就是包括a和z本身
- 在[]组成的类内部是可以连写的[a-zA-Z]
- 如果要匹配的字符中包含`-`，直接加在后面即可`[a-z-]`

### 预定义类
- `.`等价类：`[^\r\n] ` 含义：除了回车和换行之外小于两个字节（小于0xFFFF）的所有字符
- `\d`等价类：`[0-9]`  含义：数字字符
- `\D`等价类：`[^0-9]`  含义：非数字字符
- `\s`等价类：`[\t\n\x0B\f\r]`  含义：空白符
- `\S`等价类：`[^\t\n\x0B\f\r]`  含义：非空白符
- `\w`等价类：`[a-zA-Z_0-9]`  含义：单词字符
- `\W`等价类：`[^a-zA-Z_0-9]`  含义：非单词字符
常见的边界匹配的字符：<br/>
- `^`含义：以xxx开始
- `$`含义：以xxx结束
- `\b`含义：单词边界
- `\B`含义：非单词边界

### 量词
- 字符：`?` 含义：`出现零次或一次（最多出现一次）`
- 字符：`+` 含义：`出现一次或多次（最少出现一次）`
- 字符：`*` 含义：`出现零次或多次（任意次）`
- 字符：`{n}` 含义：`出现n次`
- 字符：`{n,m}` 含义：`出现n到m次`
- 字符：`{n,}` 含义：`至少出现n次`

### JS正则表达式贪婪模式和非贪婪模式
- 贪婪模式：正则表达式尽可能多的匹配，默认为贪婪模式<br/>
例：`var reg = / \d{3，6}/g`<br/>
`'12345678'.replace(reg,'X')结果为'X78'`<br/>

- 非贪婪模式：让正则表达式尽可能少的匹配，也就是说一旦匹配成功匹配不在继续尝试。<br/>
做法：在量词后加上?即可。<br/>
例：`var reg = / \d{3，6}?/g`<br/>
`'12345678'.replace(reg,'X')结果为'XX78'`<br/>

### 分组
使用()可以达到分组的功能，使量词作用于分组<br/>

或:使用`|`可以达到或的效果<br/>

反向引用：2015-12-25 => 12/25/2015<br/>
`2015-12-25.replace(/(\d{4})-(\d{2})-(\d{2})/g,'$2/$3/$1')`<br/>

忽略分组：不想捕获某些分组，只需在分组内加?:即可<br/>
例：`(?:\d{2})`表示忽略此分组<br/>

### 前瞻
正则表达式从文本头部向尾部开始解析，文本尾部方向，称为“前”。<br/>
前瞻就是正则表达式匹配到规则时，向前检查是否符合断言，后顾/后瞻方向相反<br/>
注：JavaScript不支持后瞻<br/>
符合和不符合特定断言称为肯定/正向匹配和否定/负向匹配<br/>
- 正向前瞻：`exp(?=assert)`<br/>
例：`a2*34vv.replace(/\w(?=\d)/g,'X')结果为'X2*X4vv'`
注：断言部分不属于匹配的字符，只是判断规则
- 负向前瞻：`exp(?!assert)`<br/>
- 正向后顾：`exp(?<=assert)` JavaScript不支持<br/>
- 负向后顾：`exp(?<!assert)`JavaScript不支持<br/>

### JS正则表达式对象属性
- global:是否全文搜索，默认为flase（在后面加g开启）
- ignore case:是否大小写敏感。默认flase（在后面加i开启）
- multiline:多行搜索，默认值是false（在后面加m开启）
- lastIndex:是当前表达式匹配内容的最后一个字符的下一个位置
- source:正则表达式的文本字符串

### JS正则表达式方法
- RegExp.prototype.test(str)<br/>
作用：测试字符串参数中是否存在匹配正则表达式模式的字符串。<br/>
返回值：存在返回true，否则返回false<br/>
注：该方法使用完后会影响regExp的lastIndex属性，如果多次测试不建议使用<br/>
- RegExp.prototype.exec(str)<br/>
作用：使用正则表达式对字符串执行搜索，并将更新全局RegExp对象的属性以反应匹配结果<br/>
返回值：如果没有匹配的文本则返回null,否则返回一个结果数组：
  - index声明匹配文本的第一个字符的位置
  - input存放被检索的字符串string<br/>

非全局调用：（在非全局下lastIndex不生效）<br/>
- 调用非全局的RegExp对象的exec()时，返回数组
- 第一个元素是与正则表达式相匹配的文本
- 第二个元素是与RegExpObject的第一个子表达式相匹配（分组）的文本（如果有的话），以此类推<br/>

全局调用：除了lastIndex生效外，其余与非全局调用相同<br/>

### 字符串的对象方法
- String.prototype.search(reg)<br/>
作用：search()方法用于检索字符串字符中指定的子字符串，或检索与正则表达式相匹配的子字符串。<br/>
返回值：方法返回第一个匹配结果index，查找不到返回-1.<br/>
注：search()方法不执行全局搜索，它将忽略标志g,并且总是从字符串的开始进行检索<br/>
- String.prototype.match(reg)<br/>
作用：match()方法将检索字符串，以找到一个或多个regexp匹配的文本<br/>
注：regexp是否具有全局（g）对结果影响很大<br/>
  - 非全局调用（在非全局下lastIndex不生效）<br/>
  match()方法就只能在字符串中执行一次<br/>
  返回值：如果没有任何匹配的文本，返回null,否则返回一个数组，其中存放了与他找到的匹配文本有关的信息<br/>
  说明:返回数组的第一个元素存放的是匹配文本，其余元素存放与正则表达式的子表达式（分组）匹配的文本
    - index声明匹配文本的起始字符在字符串的位置
    - input声明对stringObject的引用<br/>
  - 全局调用<br/>
  match()方法将执行全局检索，找到字符串中的所有匹配字符串<br/>
  返回值：如果没有任何匹配的文本，返回null,如果找到了一个或者多个匹配子串，则返回一个数组<br/>
  说明：返回的数组中存放的是字符串中所有的匹配子串，而且也没有index属性或者input属性
- String.prototype.split(reg)<br/>
作用：把字符串分割为字符数组<br/>
例如：`'a1b2c3d4'.split(/\d/g)结果为['a','b','c','d']`<br/>
- String.prototype.replace(str,replaceStr)<br/>
例如：`'a1b'.replace('1',2)结果为'a2b'`<br/>
例如：`'a1b1c1'.replace('1',2)结果为'a2b1c1'`<br/>
- String.prototype.replace(reg,replaceStr)<br/>
例如：`'a1b'.replace(/1/g,2)结果为'a2b2c2'`<br/>
- String.prototype.replace(reg,function)<br/>
function参数含义（function会在每次替换的时候调用，有4个参数）：
  - 匹配字符串
  - 正则表达式分组内容，没有分组则没有该参数（有多个分组择优多个参数）
  - 匹配项在字符中的index
  - 原字符串

例如：'a1b2c3d4' => 'a2b3c4d5'<br/>
`'a1b2c3d4'.replace(/\d/g,function(match,index,origin){retrun parseInt(match)+1;})结果为'a2b3c4d5'`<br/>
