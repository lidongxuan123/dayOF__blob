---
title: 生成token，并把token加入到前端请求头中
date: 2020-04-23 10:09:37
tags: token的生成和使用
categories: npm包知识
---

# token的生成
> npm i jsonwebtoken -- save

> token的生成
```
var jwt = require("jsonwebtoken)
var token = jwt.sign({
    key: value,
}, "xxxx")
```
# token的使用
> 前端定在登录的时候把返回的token定义为全局变量，然后在每次发送请求的时候在请求头中把token加入到里面，后端通过token可以方便操作数据库
> 例子一
    var xhr = new XMLHttpRequest()
    xhr.open("get", "/api/sendMsg")
    xhr.setRequestHeader("token", token)

> token每次会发生变化,当退出重新登录的时候会重新生成一个新的,此时后端需要把这条token值删除