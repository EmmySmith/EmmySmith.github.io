---
title: 从0到1搭建Hexo for Mac 主题配置(二)
date: 2019-03-21 19:21:15
tags: base
categories: blog
summary_img: /image/second.gif
---


##### 由从0到1搭建Hexo for Mac 基础(一)的搭建完成，接下来选择一个好的主题是很有必要的


**Hexo官网：[Hexo Website](https://hexo.io/themes),本人也是在网上看了很多，找了适合的主题：next，本文主要是以next为例进行搭建Hexo的主题配置**


## 1. 下载主题
* 切换到blog目录下，运行命令行进行下载主题`git clone https://github.com/iissnan/hexo-theme-next themes/next`
* ![EmSVv4.png](https://s2.ax1x.com/2019/04/26/EmSVv4.png)

## 2.配置主题细节
### 2.1 修改配置文件
* 打开文件中的配置文件`_config.yml`，将文件中的76行theme修改问`next`
 ![EmSHsJ.png](https://s2.ax1x.com/2019/04/26/EmSHsJ.png)
 
### 2.2 修改语言、标题及个性化图像
* 打开文件中的配置文件`_config.yml`,修改文件中的语言`language`,标题`title`,个性化图像`avator`
![EdKmlD.png](https://s2.ax1x.com/2019/05/04/EdKmlD.png)

### 2.3 添加标签和分类
* 打开主题下的配置文件`_config.yml`,去掉注释文件中的标签`tags`和分类`categories`
![EdlrtI.png](https://s2.ax1x.com/2019/05/04/EdlrtI.png)
* 在`../source/_posts`文件中编写属于自己的blog，前置标记带有特点的`tags`
![E0cx3t.png](https://s2.ax1x.com/2019/05/05/E0cx3t.png)
* 在blog网址上能看到带有特殊标记的文章便于搜索
![E0g0Ve.png](https://s2.ax1x.com/2019/05/05/E0g0Ve.png)

### 2.4 侧边栏的社交链接
* 侧边栏中的社交链接包含两个部分，链接和图标，在主题下配置文件中的`_config.yml`
* 链接`Social Links`中修改需要分享的链接就去掉`#`标志，加上自己的链接
![E0p4Yj.png](https://s2.ax1x.com/2019/05/05/E0p4Yj.png)

* 图标`Social Icons`中对应链接一一匹配，需要的就去掉`#`标志，设定链接的图标，加上对应的字段。其键值格式是匹配建---图标名称
![E0pqmT.png](https://s2.ax1x.com/2019/05/05/E0pqmT.png)

### 2.5 添加背景图
* 为了让blog整体效果看的更炫酷点，加上背景图片是很有必要的，在`/blog/themes/next/source/images`下加入以`.jpg`结尾的图片
![EBisFU.png](https://s2.ax1x.com/2019/05/06/EBisFU.png)

* 在主文件下的`/blog/themes/next/source/css/_custom/custom.styl`中加入`css`代码

```
body {
  background: url(/images/background.jpg);
  background-attachment: fixed;
}
```
### 2.6 使用不蒜子站点统计
* 使用的[不蒜子](https://busuanzi.ibruce.info/)统计，何为不蒜子简言之就是`两行代码 搞定计数`
* 修改方法，在`next`文件夹下的`blog/themes/next/_config.yml`修改`script`为

```
busuanzi_count:
  # count values only if the other configs are false
  enable: true
  # custom uv span for the whole site
  site_uv: true
  site_uv_header: 访客数
  site_uv_footer: 人
  # custom pv span for the whole site
  site_pv: true
  site_pv_header: 总访问量
  site_pv_footer: 次
  # custom pv span for one page only
  page_pv: true
  page_pv_header: <i class="fa fa-file-o"></i>  阅读数
  page_pv_footer:

```

### 2.7 文章摘要设置
* 在左侧首页标签栏下，设置文章摘要方便显示文章预览，看起来更美观
* 在主题配置文件中的`blog/themes/next/_config.yml`修改`enable: flase`改为`enable: true`如下：

```
# Automatically Excerpt. Not recommend.
# Please use <!-- more --> in the post to control excerpt accurately.
auto_excerpt:
  enable: true
  length: 150
```

### 2.8 首页添加封面图
* 刚刚文章首页已经设置摘要，再添加封面图效果更佳：在首页每篇文章中都会显示一个图片(可以是静态或动态)，打开文章详情页就不显示该图片
* 在每篇文章中开头添加`summary_img`,如下显示
[![EjJbLV.png](https://s2.ax1x.com/2019/05/19/EjJbLV.png)](https://imgchr.com/i/EjJbLV)
* `hexo`默认不支持`summary_img`字段，需要在主题配置文件中`/themes/next/layout/_macro/post.swig`添加如下代码

```
<!--自定义封面摘要图片  start-->
{% if post.summary_img  %}
  <div class="out-img-topic">
    <img src={{ post.summary_img }} class="img-topic">
  </div>
{% endif %}
<!--自定义封面摘要图片  end-->

```
* 添加的代码放在以下位置即可：
![EjYPL6.png](https://s2.ax1x.com/2019/05/19/EjYPL6.png)

### 2.9 分离博客源码与发布文件
* 细心的同学肯定会发现远程仓库和本地的代码不一致，自己编写的`.md`文件在远程仓库也没有显示，取而代之的是生成了`.html`静态文件
[![VGATD1.png](https://s2.ax1x.com/2019/06/02/VGATD1.png)]
* 这样导致的问题就是万一换了一个电脑，本地的`.md`文件也找不到，远程仓库也没有这就很尴尬，莫慌有个方法可以解决这个问题。需要将原始文章和发布生成的静态文件分离，利用`git`的分支管理可以很方便的做到
* 在进行`hexo d`后可以看到远程仓库是以`master`保存本地的文件。那具体的方法是我们先在远程的仓库中新建一个分支例如`save`用于专门存放保存原始文件的分支，在本地编写好后`push`到远程仓库中就会保存本地的文件（也就是`.md`文件不会丢失），切换到本地的`blog`根目录下，具体操作的步骤如下

```
git init    初始化本地文件
git remote add origin https://github.com/EmmySmith/EmmySmith.github.io.git    添加远程仓库
git checkout -b save   新建 save 分支
git add .           将所有的代码提交到缓存区   
git commit -m 'new branch save'   提交分支代码
git push          推送到远程
```
* 以上的所有操作是不是觉得有点冗余，是的。为了方便每次提交代码的方便，可以写一个`npm`帮助我们做这些事。在根目录下的`package.json`文件中加入以下执行代码：
```
"scripts": {
    "pub": "git checkout save && hexo clean &&  hexo g && hexo d && git add . && git commit -m 'update' && git push"
  },
```
* 添加完成后执行`npm run pub`命令就能自动完成`分离博客源码与发布文件`的事。主要的步骤为`1.切换到save分支->2.生成并发布博客->3.将所有修改全部推送到远程分支中`











### 参考文章 
 * [Mac 系统下搭建hexo个人博客](https://www.jianshu.com/p/77db3862595c)
 * [hexo页脚添加访客人数和总访问量](https://www.jianshu.com/p/c311d31265e0)
  