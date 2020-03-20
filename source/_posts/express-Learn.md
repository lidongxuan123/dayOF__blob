---
title: express-Learn & express框架学习
date: 2019-12-17 09:10:39
tags: express框架学习
categories: 
- express框架学习
---

# Express学习
1. 获取请求中相关数据（req)
> req.app: 当callback为外部文件时，用req.app访问express的实例
> req.baseUrl: 获取路由当前安装的URL路径
> req.body: post请求体数据
> req.hostname/req.ip: 主机名和IP
> req.originalUrl: 获取原始请求url
> req.params: 获取路由的parameters
> req.path: 获取请求路径
> req.protocol: 获取协议类型
> req.query: 获取get请求的数据
> req.route: 获取当前匹配的路由
> req.accepts:可接受的请求文档类型

# 数据返回
> res.app: 
> res.append: 追加指定HTTP头
> res.set()在res.append()后将重置之前设置的头
> res.cookie(name, value, [option]): 设置Cookie
> res.clearCookie():清除cookie
> res.download(): 下载文件
> res.get():返回指定的http头
> res.sendFile(path, options, fn): 发送文件
> res.status: 设置http状态码
> res.type: 设置content-type的mime类型

# express知识点
1. 静态资源托管
> express.static(root, [options]) *root为静态资源所在的目录，options是可选的*
2. 模板引擎
> app.engine(ext, callback)
> app.engine('jade', require('jade').__express)
> app.engine('html', require('ejs').__renderFile)