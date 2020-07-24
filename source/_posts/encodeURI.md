---
title: encodeURI（前端请求URL编译）
date: 2020-07-20 18:13:13
tags:  js前端请求URL
categories:
- 
---

# 问题：
> 前端开发过程中，接口路径中包含特殊字符。（;/?:@&=+$,#，[],{}）等
# 解决方法
> 使用javascript中的encodeURI() 函数对特殊字符及逆行转义
1. 使用
encodeURI方法不会对（;/?:@&=+$,#）进行转义，但是会对（{}，[]）转义
如果要对（;/?:@&=+$,#，{}，[]）都转义，请使用encodeURIComponent()
2. 编码与解码
encodeURI()、decodeURI()、encodeURIComponent()、decodeURIComponent()

> decodeURI() 解码某个编码的URI
> decodeURIComponent() 解码一个编码的URI
> encodeURI() 把字符串编码为URI
> encodeURIComponent() 把字符串编码为URI组件

总结： encodeURI和encodeURIComponent()是对字符串进行编码
decodeURI和decodeURIComponent是对字符串进行解码



