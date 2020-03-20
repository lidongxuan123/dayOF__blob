---
title: 浏览器拦截问题
date: 2019-12-02 15:38:33
tags: 浏览器拦截
categories: 
- JavaScript
---

# 浏览器拦截
1. 把javascript的window.open()声明成一个js对象,然后把指向的地址赋值给其location属性(注意如果是在Ajax回调函数里使用的话，-定要设置async成false,否则还是会被拦截掉)
# 解决方法
     
 ![alt 解决浏览器拦截问题](/images/Javascript/windowOpen/1.png)
