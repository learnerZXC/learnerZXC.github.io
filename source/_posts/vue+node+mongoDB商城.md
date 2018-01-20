---
title: vue+node+mongodb商城系统
date: {{data}}
tags:
categories:
---
# vue+node+mongodb商城系统
### Vue和React对比
Vue和React都使用了Virtual DOM
#### Vue：
- 模板和渲染函数的弹性选择
- 简单的语法及项目创建
- 更快的渲染速度和更小的体积

#### React：
- 更适用于大型应用和更好的可测试性
- 同时适用Web端和原生App
- 更大的生态圈带来的更多支持和工具

#### Vue和React相同点：
- 利用虚拟DOM实现快速渲染
- 轻量级
- 响应式组建
- 服务器端渲染
- 易于集成路由工具，打包工具及状态管理工具
- 优秀的支持和社区

### Vue概况以及核心思想
- Vue本身并不是一个框架
- Vue结合周边生态构成一个灵活的、渐进式框架</br>

核心思想：</br>
- 数据驱动
- 组件化

### 项目所使用的技术
- 前端使用Vue全家桶以及ES6</br>
前端主要采用Vue.js-MVVM渐进式框架</br>
视图层:商品列表、购物车、地址列表、商品结算、订单成功</br>
插件：公共组件、Vue-Router(路由)、Axios、VueS、Util、依赖（第三方插件）</br>
工具支持：vue-cli(生成项目模板)、webpack(构建工具)</br>
- 后端使用Express框架
- 数据库使用MongoDB

### 1.安装和搭建NodeJS和npm环境
### 2.vue环境搭建及vue-cli使用
vue多页面应用文件引入：</br>
- 官网拷贝</br>
`<script src="https://unpkg.com/vue/dist/vie.js"></script>`<br/>
- npm安装</br>
`npm install vue --save`<br/>
`<script src="node_modules/vue/dist/vue.min.js"></script>`<br/>
vue-cli构建SPA(single page application)应用<br/>
1. `npm install -g vue-cli`（使用Vue命令之前必须安装，如安装过则不需安装）<br/>
2. `vue init webpack-simple demo`或`vue init webpack demo2`<br/>
第二个命令后会出现一些要填写的选项:<br/>
`Project name(Demo)`:项目名称（不能有大写）<br/>
`Project description(A vue.js project)`:项目描述<br/>
`Author`:作者<br/>
`Vue build?(Use arrow keys)`:选择打包方式，有两种方式（runtime和standalone），使用默认即可<br/>
`Install vue-router? (Y/n)`:是否安装路由，一般都要安装<br/>
`Use ESLint to lint your code? (Y/n)`:-是否启用eslint检测规则，这里个人建议选no，因为经常会各种代码报错，新手还是不安装好<br/>
`Set up unit tests (Y/n)`:是否安装单元测试<br/>
`Setup e2e tests with Nightwatch? (Y/n)`：是否安装e2e测试<br/>

### 3.Vue配置介绍
- bulid文件夹：打包的配置文件所在的文件夹<br/>
build.js:构建生产版本<br/>
check-version:检查版本
webpack.base.conf.js:打包的核心配置<br/>
webpack.prod.conf.js:生产包的配置<br/>
- config文件夹: 打包的配置<br/>
index.js：开发的环境配置<br/>
- src:项目源码<br/>
- static:静态资源<br/>
- .babelrc:ES6编译插件的配置<br/>
- .gitignore:git忽略的地址<br/>
- .editorconfig:编辑器的配置<br/>
- .postcssrc：html添加前缀的配置<br/>
- index.html:单页面的入口<br/>
- package.json：定义了这个项目所需要的各种模块，以及项目的配置信息（比如名称、版本、许可证等元数据）。npm install命令根据这个配置文件，自动下载所需的模块，也就是配置项目所需的运行和开发环境。<br/>
scripts:脚本命令<br/>
dependencies:项目的依赖库<br/>
devDependencies:开发依赖库(打包好之后就不需要了)<br/>
engines：引擎<br/>

### 4.Vue基础语法<br/>
1. 模板语法<br/>
- Mustache语法：{{ msg }}<br/>
- Html赋值：`v-html=""`<br/>
- 绑定属性：`v-bind:id=""`<br/>
- 使用表达式：`{{ ok?"Yes":"No" }}`<br/>
- 文本赋值：`v-text=""`<br/>
- 指令：`v-if=""`<br/>
- 过滤器：`{{ message|capitalize}}`和`v-bind:id="rawId|formatId"`<br/>

2. Class和Style绑定<br/>
- class绑定对象语法：`v-bind:class="{active: isActive,'text-danger':hasError}"`<br/>
- class绑定数组语法：<br/>
```
<div v-bind:class="[activeClass, errorClass]">

data: {
  activeClass: 'active',
  errorClass: 'text-danger'
}
```
- style绑定对象语法：`v-bind:style="{ color: activeColor, fontSize: fontSize + 'px'`<br/>

3. vue事件处理器<br/>
- `v-on:click="greet"`或`@click="greet"`<br/>

4. vue组件<br/>
- 全局组件和局部组件<br/>
- 父子组件通讯-数据传递<br/>
- Slot<br/>

### 5.Vue-router
#### 路由简介
路由：路由是根据不同的URL地址战士不同的内容或页面<br/>
前端路由：前端路由就是把不同路由对应不同的内容或页面的任务交给前端来做，之前通过服务器根据url的不同返回不同的页面实现的<br/>
什么时候使用前端路由？<br/>
在单页面应用，大部分页面结构不变，只改变部分内容的使用<br/>
前端路由的优缺点：<br/>
- 优点：用户体验好，不需要没车都从服务器全部获取，快速展现给用户<br/>
- 缺点：<br/>
  1. 不利于SEO<br/>
  2. 使用浏览器的前进，后退会重新发送请求，没有合理利用缓存、<br/>
  3. 单页面无法记住之前滚动的位置，无法在前进，后退的时候记住滚动条的位置<br/>
#### vue-router
- vue-router用来构建SPA<br/>
- <router-link></router-linl>或者this.$router.push({path:''})  路由调整<br/>
- <vouter-view></router-view>  路由渲染<br/>
- 动态路由匹配<br/>
动态路由举例：<br/>
  - 模式：`/user/:username`  匹配路径：`/user/evan` $route.params:`{username:'evan'}`<br/>
  - 模式：`/user/:username/post/post_id`  匹配路径：`/user/evan` $route.params:`{username:'evan',post_id:123}`<br/>
地址后面跟#因为路由模式用的hash,可以在Router下的index.js添加mode:'history'改变原生的URL方式<br/>
- 嵌套路由<br/>
嵌套路由即为路由嵌套路由<br/>
在路由中定义子路由（router下的index.js）<br/>
```
routes: [
   {
     path: '/goods',
     name: 'GoodsList',
     component: GoodsList,
     children:[
       {
         path: 'title',//子路径注：路径前面不能加/,否则变为一级路由
         name: 'title',
         component: Title //组件
       },
        {
         path: 'image', //子路径
         name: 'image',
         component: Image //组件
       }
   ]
   }
 ]
```

在父路由页面添加：<br/>
```
    <router-link to='/goods/title'>显示商品标题</router-link> //路径必须自己定义到父路径，并不能只写子路径
		<router-link to='/goods/img'>显示商品图片</router-link>
		<div>
			<router-view></router-view> //组件渲染载体。
		</div>
```
- 编程式路由<br/>
通过JS来实现页面的跳转<br/>
`$route.push("name")`通过名字跳转<br/>
`$route.push({path:"name"})`通过路径跳转<br/>
`$route.push({path:"name?a=123"})`或者`$route.push({path:"name"，query:{a:123}})`跳转的同时添加一些参数，获取参数用`$route.query.a`来获取<br/>
`$route.go()`相当于history.go(),vue-router是对history的封装<br/>
- 命名路由和命名视图<br/>
命名路由：给路由定义不同的名字，根据名字进行匹配<br/>
例如：
在路由中给组件命名：
```
routes: [
    {
      path: '/goods',
      name: 'GoodsList',
      component: GoodsList,
    },
    {
    	path: '/cart/:cartId',
    	name: 'cart',
    	component: Cart
    }
  ]
```
在页面中
`<router-link v-bind:to='{name:'cart',params:{cartId:'123'}}'>跳转到购物车页面</router-link>`//注：to得用V-bind绑定
命名视图：给不同的router-view定义名字，通过名字进行对应组件的渲染<br/>

### 6.Vue-Resource（异步插件）
#### 简介<br/>
- 使用方式<br/>
  1. `<script src="https://cdn.jsdelivr.net/vue.resource/1.3.1/vue-resource.min.js"></script>`<br/>
  2. `npm install vue-resource --save`<br/>
  `<script src="node_modules/vue/dist/vue.js"></script>`<br/>
	`<script src = "node_modules/vue-resource/dist/vue-resource.js"></script>`//引用vue-resource插件前要先引用vue插件<br/>
- vue-resource的请求API是按照REST风格设计的，它提供了7种请求API：<br/>
  - get(url,[options])<br/>
  - head(url,[options])<br/>
  - delete(url,[options])<br/>
  - jsonp(url,[body],[options])<br/>
  - post(url,[body],[options])<br/>
  - put(url,[body],[options])<br/>
  - patch(url,[body],[options])<br/>

### 7.了解AXIOS插件（异步请求插件）

### 8.商品列表基础组件拆分
- Header组件<br/>
- Footer组件<br/>
- 面包屑组件<br/>
组件：可以被其他页面复用的（通常放在component里面）<br/>
页面：只是自己使用的（存放在views里面）<br/>

assets和static通常用来放静态资源，assets通常用来放组件的资源，static通常放页面资源等
