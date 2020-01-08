---
title: Django入门(一)
date: 2019-11-11 19:34:13
tags: django
categories: 技术
summary_img: /image/djangoinit.gif
---

##### 最近一直在学习Django，没有做笔记，今天来总结一下简单的入门

#### 前置条件

```
1.安装Python3
2.安装Pycharm
3.安装Django包
有了这些就能学习Django
```
### 1.什么是Django
* Django是一个Python的高级Web框架，功能强大，封装了大量底层，使开发 Web 代码变得高效、快速、简洁。Django希望不重复自己，具有松耦合与灵活等特性，非常适合快速开发。Django 是一个简洁而强悍的 Web 开框架，基于 Python 语言开发，只需要少量的代码就可以快速实现强大的功能。
* 掌握Django需要理解模型（ Model）、视图（ Views）和模板（ Templates），即MTV模式，有点类似Java语言开发里面的MVC模式。模型：控制数据，如存取，关联关系等；视图：定义显示的方法、函数；模板：业务逻辑。

### 2.项目环境准备
* 接下来的命令可以直接在pycharm中操作，也可以用命令行来操作，为了操作更酷选择用命令行操作
#### 1.创建项目
* `django-admin startproject Django190507`  
#### 2.启动服务 
* 命令行`python3 manage.py runserver 127.0.0.1:8000`但也可在pycharm中设置不需要每次都输入![MQvzwT.png](https://s2.ax1x.com/2019/11/11/MQvzwT.png)
![MQx2AU.png](https://s2.ax1x.com/2019/11/11/MQx2AU.png)
通过第2个操作可以直接在pycharm中`run manage.py`。在浏览器中输入`http://127.0.0.1:8000/`后出现小火箭即为正常启动！
#### 3.创建超级用户
* `python manage.py createsuperuser`后，设置用户名(admin)、密码(test123456)、邮箱。在浏览器中输入`http://127.0.0.1:8000/admin`输入设置的用户名和密码可看到站点管理页面
[![MtB1Ff.md.png](https://s2.ax1x.com/2019/11/14/MtB1Ff.md.png)](https://imgchr.com/i/MtB1Ff)
#### 4.汉化中文
* 用pycharm打开创建的项目，打开`setting.py`修改成如下
```
# LANGUAGE_CODE = 'en-us'

# TIME_ZONE = 'UTC'

LANGUAGE_CODE = 'zh-Hans'

TIME_ZONE = 'Asia/Shanghai'
```
* 以上所有的环境准备问题已经OK，接下来实现简单的`Django`模型

### 3.实现入门的项目
####    1. 创建应用
* `Python manage.py startapp apitest`后，把创建的应用添加到`settings.py`中的`INSTALLED_APPS`中,注意以逗号结尾
```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'djcelery',
    'apitest',
]
```

#### 2.  创建视图
* 在`views`中加入`test`函数
```
from django.shortcuts import render
from django.http import HttpResponse #加入引用
# Create your views here.
def test(request):
    return HttpResponse("hello test") #返回 HttpResponse 响应函数
```
#### 3. 创建映射
* 映射是指把视图中的函数映射到浏览器前端页面，在页面中能显示，故在`Django190507/urls.py`中加入
```
from django.contrib import admin
from django.urls import path
from apitest import views #加入引用
urlpatterns = [
    path('admin/', admin.site.urls),
    path('test/', views.test), #加入关联路径及函数
]
```
* 在浏览器中输入 127.0.0.1:8000/test，即看到函数返回响应数据
![MTn5hF.png](https://s2.ax1x.com/2019/11/22/MTn5hF.png)
以上就是关于Django的基础入门，(环境准备、创建基础项目),接下来章节继续讨论...

