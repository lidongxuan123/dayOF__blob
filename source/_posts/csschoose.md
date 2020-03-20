---
title: css选择器
date: 2019-11-14 10:11:55
tags: css选择器
categories: 
- web前端css
---

# CSS选择器
1. css高级选择器
    | css | 例子 | 解释 |
    | ---- | ---- | ---- |
    | [attribute] | [title] | 选择所有包含title属性的元素 |
    | [arrtibute = value]  | [title="heard"]   | 选择属性titlede等于heard的元素 |
    | [attribute ~=value]  | title~=heard   | 选择title包含heard的元素 |
    | :link   | a:link   | 选择所有未访问链接 |
    | :visited  | a:visited   | 选择所有访问过的链接 |
    | :active  | a:active  | 选择活动链接 |
    | :focus  | input:focus   | 选择具有焦点的输入元素 |
    | :first-letter  | p:first-letter   | 选择每一个p元素的第一个字母 |
    | :first-line  |  p:first-line  | 选择p元素的第一行 |
    | element1~element2  | p~ul  | 选择p元素之后的每一个ul元素 |
    | [attribute^=value]  | a[src^="https"]   | 选择每一个src属性的值以"https"开头的元素 |
    |  [attribute$=value] |  	a[src$=".pdf"]  | 选择每一个src属性的值以".pdf"结尾的元素 | 
    |  [attribute*=value] |  	a[src*="runoob"]  |选择每一个src属性的值包含子字符串"runoob"的元素 |

```
[attribute]    选择所有包含
```


