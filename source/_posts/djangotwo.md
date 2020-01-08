---
title: Django入门(二)
date: 2019-11-23 12:34:13
tags: django
categories: 技术
summary_img: /image/djangotwo.gif
---



#### 4.创建模板
* 创建模板能在前端显示页面，在`apitest`中创建`templates`文件夹后创建`login.html`文件,纯HTML5页面，后续详细介绍前端知识
```
<!DOCTYPE html>
    <html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
        <title>Login</title>
</head>
<body>
<h1>login</h1>
<form method="post" action="/login/">
{% csrf_token %}
<br> <input name="username" type="text" placeholder="username" >
<br> <input name="password" type="password" placeholder="password">
{{ error }}<br>
<br> <button id="submit" type="submit">submit</button>
</form>
</body>
</html>

```