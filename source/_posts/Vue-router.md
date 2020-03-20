---
title: Vue-router 两种路由方式
date: 2020-03-19 19:15:54
tags: Vue-router 两种路由方式
categories:
- Vue项目知识
---

# vue-router知识
<span style="color:red">
http://1227.0.0.1:8080/别名
路由访问的时候可以在跟目录下加别名的方式来访问相对应的路由</span>  

> 两种解决嵌套路由的方式
1. alias: '/', 每个路由里面都加一个alias
```
 path: "studentMangement",
    name: 'studentMangement',
    alias: '/',
    flag: true,
    component: studentMangement,
    children: [{
        path: "list",
        name: 'studentMangementList',
        alias: '/',
        flag: true,
        component: studentMangementList
    }]
```
2. redirect: {path: "XXXX"} 父路由通过alias和redirece来实现
```
{
    path: '/a',
    alias: '/',
    name: 'a',
    component: a,
    redirect: {path:'/a/b'},
    children: [{
      path: 'b',
      name: 'b',
      component: b,
      redirect: {path: "/a/b/c"},
      children: [{
        path: 'c',
        name: 'c',
        component: c
      }]
    }, {
        path: 'd',
        alias: "/",
        name: 'd',
        component: d
      }]
  },
```
# 示例
![示例](./images/vue-router-redirect.png)