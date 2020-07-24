---
title: egg.js 内置对象
date: 2020-07-23 14:21:05
tags: egg.js内置对象
categories: 
- Egg
---
# egg.js 内置对象
1. application
application 全局对象，可以挂载一些全局方法和对象

app.js  
```
module.exports = app =>{
    app.once()
}
```
controller文件
```
const {ctx config} = this
this.app.config.xxx
```

2. context
context请求级别对象，这个对象封装了这次用户请求的信息，
获取未知： middleware，controller，service中
获取方式为： const {ctx config} = this

3. request response
request，response是一个请求对象，
获取方式： ctx.request  ctx.response

4. controller
框架提供了一个controller基类，
controller基类有下列属性
const {ctx, app, config, service, logger} = this

5. 框架提供了一个service基类，并推荐所有的service都继承该基类













