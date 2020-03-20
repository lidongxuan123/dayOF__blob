---
title: Vue中路由的使用
date: 2019-11-22 09:29:29
tags: Vue中路由this.$route.push和replace的区别
categories: 
- Vue项目知识
---

# this.$route.query和this.$route.params
1. this.$route.query的使用
```
>传值
this.$router.push({
    path: "路径",
    query: {
        id: 'id'
    }
})
> 接收
this.$route.query.id
> 表现形式
http://..../#/路径?id="id"
```
**this.$route.query使用：页面之间用路由跳转传值时，刷新跳转后传参的页面，数据还会显示**

2. this.$route.params的使用
```
> 传值
this.$router.push({
    name: "name",  // 或者 path: "url"
    params: {
        id: "id"
    }
})
> 接收值
this.$route.params.id
> 表现形式
http://...../monitor
```
**this.$route.params使用场景：页面之间用路由跳转传参时，刷新跳转后传参的页面，数据不存在**

# this.$router.push 和 this.$router.replace的区别

1. this.$router.push()
> **描述：**跳转到不同的url,但是这个方法会向history栈添加一个记录 ，点击退回会返回到上一个页面
2. this.$router.replace()
> **描述：**这个方法也是跳转到指定的路径，但是这个方法不会向history里添加记录，点击返回也不会跳到上一个页面。
3. this.$router.go(n)
> **描述：**相当于页面向前或者向后跳转多少个页面

