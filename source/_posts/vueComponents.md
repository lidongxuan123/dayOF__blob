---
title: vue组件传值watch和mounted
date: 2020-01-07 11:21:19
tags: vue组件传值
categories: 
- Vue项目知识
---

# 父组件传值
> 父组件传值是变化的
1. mounted 只能使用组件第一次加载的父组件传来的值，当父组件传来的值发生变化后，只能通过watch监听值的变化，从而进行后续的运算。
2. 组件第一次加载的时候，不会触发watch里的函数
3. 方法里可以直接使用传递后的值