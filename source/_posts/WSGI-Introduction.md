---
title:  WSGI介绍
date: 2018-02-22 22:04:59
tags: Openstack,WGSI
---

最近在看cinder的代码,但是一上来被代码结构搞的很糊涂,不知道如何看起,我们都知道openstack的组件对外提供的是RESTful API,也就是HTTP请求,在Python里WSGI可以算得上是很重要的一个概念了，所以就先了解下WSGI。
<!--more-->

WSGI的全称为Web Server Gateway Interface,一个看上去很笼统的名字,但是如果了解过Java的话，就可以拿Java里面的Servlet来类比Python中的WSGI，Servlet和WSGI一样都是只是一种标准，具体的实现在各个Web容器之中，就像Servlet中要实现doGet(request,response)或者doPost(request,response)一样,WSGI中也要实现一个函数，这个函数的名字是可以自定义的，但是入参是定好的，为environ, start_response。

environ为一个包含所有HTTP请求信息的`dict`对象。

start_response为一个发送HTTP响应的函数。

一般一个HTTP的请求类型或者一种资源的请求会被一个函数结束，术语称为应用或者application。

一个应用是由多个application组成的，如何通过不同的URL访问不同的application，这需要后面介绍的paste,Routes。

今天就先把一个简单的WSGI运行起来吧。

我们先编写hello.py，实现Web应用程序的WSGI处理函数：
```python
# -*- coding: utf-8 -*-
# hello.py
def application(environ, start_response):
    start_response('200 OK', [('Content-Type', 'text/html')])
    return [b'<h1>Hello, web!</h1>']

```
然后，再编写一个server.py，负责启动WSGI服务器，加载application()函数：
```Python
# -*- coding: utf-8 -*-
# server.py
# 从wsgiref模块导入:
from wsgiref.simple_server import make_server
# 导入我们自己编写的application函数:
from hello import application

# 创建一个服务器，IP地址为空，端口是8000，处理函数是application:
httpd = make_server('', 8000, application)
print('Serving HTTP on port 8000...')
# 开始监听HTTP请求:
httpd.serve_forever()
```
确保以上两个文件在同一个目录下，然后在命令行输入python server.py来启动WSGI服务器：
![](https://cdn.qianlaofei.cn/18-2-22/51689383.jpg)
并访问
![](https://cdn.qianlaofei.cn/18-2-22/86191504.jpg)

一个简单的WSGI demo就能简单地完成了，但是系统性地使用还用WSGI还是得用框架才能更好的发挥他的作用。



