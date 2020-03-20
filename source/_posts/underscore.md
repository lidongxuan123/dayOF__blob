---
title: underscore包
date: 2020-01-07 14:28:44
tags: underscore包，实现函数式编程
categories: 
- npm包知识
---

# underscore 介绍
> Query在加载时，会把自身绑定到唯一的全局变量$上，underscore与其类似，会把自身绑定到唯一的全局变量_上，这也是为啥它的名字叫underscore的原因。
# underscore的使用
```
var _ =require("underscore")

遍历数组
_.map([1,2,3],(x)=>x*x) //结果为[1,4,9]

遍历对象
_.map({a:1,b:2,c:3},(v,k)=>k+"="+v)//结果为 ['a=1', 'b=2', 'c=3']


```



