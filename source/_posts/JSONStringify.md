---
title: JSONStringify
date: 2019-11-22 09:13:49
tags: JSON.Stringify的使用方式
categories: 
- JavaScript
---

# JSON.stringify 的使用方式

> 将javascript对象或者数组转换为JSON字符串，如果指定了 replacer 是一个函数，则可以选择性地替换值，或者如果指定了 replacer 是一个数组，则可选择性地仅包含数组指定的属性。

[JSON.stringify(MDN解释)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify)
> 语法：JSON.stringify(value[, replacer [, space]])
**value**
> 将要序列化成 一个 JSON 字符串的值。
**replacer**
> 如果该参数是一个函数，则在序列化过程中，被序列化的值的每个属性都会经过该函数的转换和处理；如果该参数是一个数组，则只有包含在这个数组中的属性名才会被序列化到最终的 JSON 字符串中；如果该参数为 null 或者未提供，则对象所有的属性都会被序列化；
**space**
> 指定缩进用的空白字符串，用于美化输出（pretty-print）；如果参数是个数字，它代表有多少的空格；上限为10。该值若小于1，则意味着没有空格；如果该参数为字符串（当字符串长度超过10个字母，取其前10个字母），该字符串将被作为空格；如果该参数没有提供（或者为 null），将没有空格。
