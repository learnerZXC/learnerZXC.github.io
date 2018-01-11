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
`<script src="https://unpkg.com/vue/dist/vie.js"></script>`
- npm安装</br>
`npm install vue --save`<br/><
`<script src="node_modules/vue/dist/vue.min.js"></script>`
vue-cli构建SPA(single page application)应用
1. `npm install -g vue-cli`
2. `vue init webpack-simple demo`或`vue init webpack demo2`
第二个命令后会出现一些要填写的选项:
`Project name(Demo)`:项目名称（必须全是小写）
`Project description(A vue.js project)`:项目描述
`Author`:作者
`Use sass?(y/N)`
