---
title: hexoBlog托管在coding
date: 2017-11-02 08:02:55
tags: hexoBlog
categories: hexo
---
# 将Hexo托管到coding上
1.如果没有coding账号，先注册。

2.在coding上创建一个项目（建议项目名和用户名相同），将属性设置为私有。如果第一次使用coding的话，需要设置SSH公钥。直接使用github生成的公钥即可。本地打开id_rsa.pub文件，复制其中全部内容，填写到SSH_RSA公钥key下的一栏，公钥名称可以随意起名字。完成后点击“添加”，然后输入密码或动态码即可添加完成。

<!--more-->

3.获取这个项目的SSH地址（在代码中可获取），配置hexo中的` _config.yml `的` deploy `下

3.添加后在` git bash `命令输入：

```
ssh -T git@git.coding.net
```

如果得到下面提示就表示公钥添加成功：

```
Coding.net Tips : [Hello ! You've conected to Coding.net by SSH successfully! ]
```

4.使用部署命令就可以把博客同步到coding上：

```
hexo deploy -g
 ```
## pages服务方式部署
部署博客方式有两种，第一种就是pages服务的方式，也推荐这种方式，因为可以绑定域名，而第二种演示的方式必须升级会员才能绑定自定义域名。pages方式也很简单
就是在source/需要创建一个空白文件，至于原因，是因为 coding.net需要这个文件来作为以静态文件部署的标志。就是说看到这个Staticfile就知道按照静态文件来发布。

```
cd source/
```

```
touch Staticfile
```

分支选择master，因为前面配置的分支是master,因此开启之后，也需要是master。然后看起之后就可访问了。

如果你的项目名称跟你coding的用户名一样， yourusername.coding.me就能访问博客，否则就要带上项目名：yourusername.coding.me/项目名 才能访问
推荐项目名跟用户名一样，这样就可以省略项目名了
