---
title: git push 报错问题
date: 2018-05-28 00:02:35
tags: git
categories:
---

# git push 报错问题
使用hexo搭建的个人博客，托管在GitHub上，突然又一段时间push的时候一直报错。错误如下：
```
ssh: Could not resolve hostname github.com: Name or service not known.fatal: Could not read from remote repository.
```
因为之前是好的，突然报这个错误，一脸懵逼，通过各种查，终于解决了这个问题（目前是解决的。）

问题排查：
1. 通过百度查到
```
ping github.com
```
得到一个IP地址，将他放入git的hosts中，但由于每次ping的到的IP有可能不同，当时第一次是可以得，到后面这个方法好像也不起作用。所以又继续查，终于找到了下面的方法。
2. 执行
```
ssh -T git@github.com
```
显示连接失败。好像是DNS哪里有问题（目前还不是特别清楚）。通过以下命令解决了。
- 进入命令行
- 输入
```
ipconfig /flushdns
```
释放DNS缓存。
- 输入
```
netsh winsock reset
```
重置Winsock目录。
- 重启计算机，就Ok了。
