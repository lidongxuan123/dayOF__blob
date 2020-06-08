---
title: call Apply Bind的使用方法
date: 2020-05-26 15:43:41
tags: call Apply Bind的使用方法
categories: 
- JavaScript
---
# Call Apply Bind 的使用方法
![Call Apply Bind 的使用方法](images/Javascript/callApplyBind/call.png)

# 微妙的差距！

从上面四个结果不难看出:

call 、bind 、 apply 这三个函数的第一个参数都是 this 的指向对象，第二个参数差别就来了：

call 的参数是直接放进去的，第二第三第 n 个参数全都用逗号分隔，直接放到后面 obj.myFun.call(db,'成都', ... ,'string' )。

apply 的所有参数都必须放在一个数组里面传进去 obj.myFun.apply(db,['成都', ..., 'string' ])。

bind 除了返回是函数以外，它 的参数和 call 一样。

当然，三者的参数不限定是 string 类型，允许是各种类型，包括函数 、 object 等等