---
title: class与style绑定
date: 2020-03-06 17:16:52
tags: class与style绑定
categories: 
- ElementUI
---
# ##Class_style
1. {类名：true/false} (对象形式单个)
2. {类名：true/false,类名：true/false} (对象形式多个)
3. :class="string"  
    String: {
        a: true/false,
        b: true/false
    }
4. :class=[a,b] 数组形式
    {
        a: 类名,
        b: 类名
    }

5. 根据判断切换class
class = [xxx? a:b]
{
    a: 类名,
    b: 类名
}
