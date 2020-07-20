---
title: Koa
date: 2020-06-30 14:38:38
tags:
categories: 
- koa
---

#Koa知识点总结

1. ctx.respond
为了绕过Koa内置的response处理，可以显示的设置ctx.respond = false,
如果你想要写入原始的res对象，而不是让koa处理你的response, 请使用此参数
koa不支持上述功能，这可能会破坏koa中间件和koa本身的预期功能。

2. ctx.request.ips（不懂）
 当X-forwarded-For 存在并且app.proxy被启用时，这些ips的数据被返回。从上游-》下游排序


#koa 中间件的使用
基本信息认证： koa-basic-auth

lesky: 轻量级Express-ish(koa) 服务器输入更多信息，用于提供静态文件和初始化工作区的CLI

koa-scoket2

koa-connect  挂在express/Connect中间件

koa2-validation: 用于校验输入值

koa-exception： koa异常处理

koa2-request-middleware: koa请求中间件





