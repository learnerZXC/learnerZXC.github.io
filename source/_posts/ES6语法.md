---
title: ES6语法
date: {{data}}
tags: ES6语法
categories:
---

## ES6语法
说明：ES6强制开启严格模式。严格模式变量未声明不能引用报引用错误。
###### 变量声明方式<br/>
- 块作用域：任何一对花括号（｛｝）中的语句集都属于一个块，在这之中定义的所有变量在代码块外都是不可见的，我们称之为块级作用域。<br/>
- let let声明的变量是在块作用域有效。<br/>
说明：let不能重复声明变量<br/>
- const const声明的常量是不能修改的，也是在块作用域有效。<br/>
注：const声明的时候必须赋值。console声明对象，是引用属性的，指针不会改变。<br/>

######  解构赋值<br/>
ES6变量的解构赋值本质上是“模式匹配”,只要等号两边的模式相同，左边的变量就会被赋予匹配的右边的值，如果匹配不成功变量的值就等于undefined<br/>
如下面的例子：<br/>

`{
  let a,b,rest;
  [a,b]=[1,2];
  console.log(a,b);
} // 1,2`<br/>

`{
  let a,b,rest;
  [a,b,...rest]=[1,2,3,4,5,6];
  console.log(a,b,rest);
} //1, 2, [3, 4, 5, 6]`<br/>

`{
  let a,b;
  ({a,b}={a:1,b:2})
  console.log(a,b);
}  // 1,2`<br/>

`{
  let a,b,c,rest;
  [a,b,c=3]=[1,2];
  console.log(a,b,c);
}  //1,2,3`<br/>

`{
  let a=1;
  let b=2;
  [a,b]=[b,a];
  console.log(a,b);
} // 2,1`<br/>

`{
  function f(){
    return [1,2]
  }
  let a,b;
  [a,b]=f();
  console.log(a,b);
} // 1,2`<br/>

`{
  function f(){
    return [1,2,3,4,5]
  }
  let a,b,c;
  [a,,,b]=f();
  console.log(a,b);
} // 1,4`<br/>

`{
  function f(){
    return [1,2,3,4,5]
  }
  let a,b,c;
  [a,,...b]=f();
  console.log(a,b);
} // 1,[3,4,5]`<br/>

`{
  let o={p:42,q:true};
  let {p,q}=o;
  console.log(p,q);
 } // 42,true`<br/>

`{
  let {a=10,b=5}={a:3};
  console.log(a,b);
} //3 ,5`<br/>

`{
  let metaData={
    title:'abc',
    test:[{
      title:'test',
      desc:'description'
    }]
  }
  let {title:esTitle,test:[{title:cnTitle}]}=metaData;
  console.log(esTitle,cnTitle);
} // abc,test`<br/>

###### 正则扩展
JavaScript正则扩展详细讲解了正则表达式及ES6新增内容

###### 字符串扩展
字符串新增特性：<br/>
- Unicode表示法<br/>
主要处理大于0xFFFF的字符<br/>
例如：<br/>
`console.log('a',`\u0061`);//a,a`<br/>
`console.log('s',`\u20BB7`);//s ₻7`因为大于0xFFFF，所以无法正常显示。<br/>
ES6中，可以用{}把Unicode编码包起来表示一个<br/>
例如：`console.log('s',`\u{20BB7}`);//s 𠮷`<br/>  

- 遍历接口<br/>
在ES6中遍历操作特质for….of循环。<br/>
在ES6中，一个对象只要部署了next方法，就被视为是具有了iterator接口，就可以用for…of循环遍历它的值。<br/>
例如：<br/>
`{`<br/>
&nbsp;&nbsp;`let str='\u{20bb7}abc';`<br/>
&nbsp;&nbsp;`for(let i=0;i<str.length;i++){`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`console.log('es5',str[i]);//不能正确识别{20bb7}`
<br/>
&nbsp;&nbsp;`}`<br/>
&nbsp;&nbsp;`for(let code of str){`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`console.log('es6',code);//识别{20bb7}为𠮷`
<br/>
&nbsp;&nbsp;`}`<br/>
`}`<br/>

- 模板字符串<br/>
ES5中要把多个字符串连接起来，可以用+号连接：如果有很多变量需要连接，用+号就比较麻烦。ES6新增了一种模板字符串，会自动替换字符串中的变量。<br/>
例如：<br/>
`let name="list";`<br/>
`let info="hello world";`<br/>
`let m=`i am ${name},${info}`;`<br/>
`console.log(m);//结果为i am list,hello world`<br/>

- 标签模板

- 新增方法<br/>
  - str.codePointAt():能够正确处理4个字节储存的字符，返回指定索引出一个字符的码点。codePointAt方法返回的是码点的十进制值，如果想要十六进制的值，可以使用toString方法转换一下。
  例如：<br/>
  `let s='𠮷';`<br/>
  `console.log('length',s.length);//length,2`<br/>
  `console.log('0',s.charAt(0));//0,�`<br/>
  `console.log('1',s.charAt(1));//1,�`<br/>
  `console.log('at0',s.charCodeAt(0));//at0,55362`<br/>
  `console.log('at1',s.charCodeAt(1));//at1,57271`<br/>
  上面两个方法不能正确处理四个字节（大于0xFFFF）的字符，而ES6中新增的codePointAt()则能很好的处理<br/>
  `let s1='𠮷a';`<br/>
`  console.log('length',s1.length);//length，3`<br/>
  `console.log('code0',s1.codePointAt(0));//code0，134071`<br/>
  `console.log('code0',s1.codePointAt(0).toString(16));//code0，20bb7`<br/>
  `console.log('code1',s1.codePointAt(1));//code1，57271`<br/>
  `console.log('code2',s1.codePointAt(2));//code2，97`<br/>
  - str.fromCodePoint()：通过Unicode码值转换对应的字符<br/>
  与es5的String.fromChartCode()相比，他可以识别四个字节 字符（Unicode编号大于0xFFFF）。<br/>
  例如：<br/>
   `console.log(String.fromCharCode("0x20bb7"));//ஷ`<br/>
   `console.log(String.fromCodePoint("0x20bb7"));//𠮷`<br/>
  - str.includes():返回一个布尔值，表示某个字符串是否包含给定的字符。
   例如:<br/>
   `let str = "string"`<br/>
   `console.log(str.includes("r"))//结果为true`<br/>
  - str.startsWith():给定文本出现在字符串开头时返回 true，否则返回 false 。<br/>
   例如:<br/>
   `let str = "string"`<br/>
   `console.log(str.startsWith("str"))//结果为true`<br/>
  - str.endsWith():给定文本出现在字符串末尾时返回 true，否则返回 false 。<br/>
   例如:<br/>
   `let str = "string"`<br/>
   `console.log(str.endsWith("g"))//结果为true`<br/>
  - str.repeat():字符串复制<br/>
   例如:<br/>
   `let str = "ab"`<br/>
   `console.log(str.repeat(3))//结果为ababab`<br/>
  - Sring.raw：往往用来充当模板字符串的处理函数，返回一个斜杠都被转义（即斜杠前面再加一个斜杠）的字符串，对应于替换变量后的模板字符串。<br/>
   例如：<br/>
   `console.log(String.raw`Hi\n${1+2}`//Hi\n3);`<br/>
   `console.log(`Hi\n${1+2}`//Hi(换行)3);`<br/>
  - str.padStart():向前补白<br/>
  例如：<br/>
   `console.log('1'.padStart(2,'0'));//结果为01`<br/>
   注：第一个参数2为输出字符串的长度，第二个为补白的字符串<br/>
  - str.padEnd():向后补白<br/>
   例如：<br/>
    `console.log('1'.padEnd(2,'0'));//结果为10`<br/>
    注：第一个参数2为输出字符串的长度，第二个为补白的字符串

   多行字符串：由于多行字符串用\n写起来比较费事，所以最新的ES6标准新增了一种多行字符串的表示方法，用反引号 \` 多行内容\` 表示：
