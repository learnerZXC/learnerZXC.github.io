---
title: SpringBoot
date: 2018-03-09 16:51:21
tags:
categories: SpringBoot
---

# SpringBoot

### 简介
Spring Boot是由Pivotal团队提供的全新框架，其设计目的是用来简化新Spring应用的初始搭建以及开发过程。该框架使用了特定的方式来进行配置，从而使开发人员不再需要定义样板化的配置。

### 特点
- 化繁为简，简化配置

### 快速创建项目

#### maven构建项目

1. 访问http://start.spring.io/

2. 选择构建工具 `Maven Project`、编程语言`Java`、SpringBoot版本以及一些工程的基本信息。点击下方的`Switch to the full version`可以选择更多的信息以及勾选相关组件。

3. 点击`Generate Project`下载项目压缩包。

4. 解压后，使用Eclipse,Import———>Maven——>Existing Maven Projects ——>Next
——>选择解压后的文件夹-> Finsh

### 项目结构介绍

- `src/main/java`: 程序开发以及主程序入口
- `src/main/resource`: 配置文件
- `src/test/java`: 测试程序

另外，SpringBoot建议目录如下：

1. Application.java: 建议放在根目录下，主要用于一些框架配置

2. domain目录主要用于实体（Entity）与数据访问层（Repository）

3. service 层主要是业务类代码

4. controller 负责页面访问控制

采用默认配置可以省去很多配置，当然也可以根据自己的喜欢来进行更改。

启动Application main方法，至此一个java项目搭建好了！

### 项目启动方式

- `src/main/java/包名/Application.java`中直接run运行。

- 命令行启动: 进入项目路径：`cd 项目路径`，使用命令`mvn spring-boot:run`来启动

- 命令行启动: 进入项目路径：`cd 项目路径`，编译项目`mvn install`, 进入target文件夹`cd traget`, 然后使用`java -jar 文件名`来启动
