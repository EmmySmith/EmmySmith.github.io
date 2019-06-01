---
title: 从0到1搭建Hexo for Mac 基础(一)
date: 2019-03-14 23:13:44
tags: blog
categories: base
summary_img: /image/first.jpg
---


##### 这几天自己尝试搭建了Hexo，也是参考了一些文档自己总结了一下

### 前置条件
```
1. 注册github账号
2. 安装Node
3. 安装Git
4. 安装npm
5. 全局安装hexo     npm install -g hexo-cli
```
##### 接下来我们开始搭建属于自己的blog

** **
1、 创建blog文件夹（文件名eg:blog），并初始化blog框架

```
1. mkdir blog      创建博客文件夹
2. cd blog         进入目录
3. hexo init       初始化目录
4. hexo s          开启本地服务
出现以下信息就说明可以正常访问，在浏览器中输入地址就能正常访问本地博客系统进入首页啦
```
[![kxbva6.png](https://s2.ax1x.com/2019/03/07/kxbva6.png)](https://imgchr.com/i/kxbva6)

2、 关联Github仓库

* 为什么要关联Github仓库呢，因为之前的操作我们都是在本地进行的，想要在服务器上随心所欲的看自己的博客当然要和Github仓库关联才能实现
* 首先在_config.yml文件中配置GitHub账号

[![AnTYQJ.png](https://s2.ax1x.com/2019/03/19/AnTYQJ.png)](https://imgchr.com/i/AnTYQJ)

* 打开文件（vim  _config.yml），拉到最低的 **Deployment**中填写type,repo,branch

```
1. type    默认填写git
2. repo    填写自己的远程仓库地址
3. branch  直接写master
```
[![Aukdvd.md.png](https://s2.ax1x.com/2019/03/19/Aukdvd.md.png)](https://imgchr.com/i/Aukdvd)

*  Hexo提供了快速方便的一键部署功能，让您只需一条命令就能将网站部署到服务器上，`hexo d`== `hexo deploy` ,执行`hexo d`前，先安装必要的`Git` 部署插件

```
1.  npm install hexo-deployer-git --save

```
*  最后依次执行以下命令：

```
1. hexo clean    清除缓存
2. hexo g        generate
3. hexo d        deploy
```
* 接下来就是见证奇迹的时刻了，在网址中输入**https://Github账号.github.io**,你的blog应该就正式诞生啦，恭喜💐

### 参考文章 
 * [Mac 系统下搭建hexo个人博客](https://www.jianshu.com/p/77db3862595c)