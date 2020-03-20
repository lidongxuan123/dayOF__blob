---
title:  vercial-align(图片与span竖直居中)
date: 2019-11-07 19:23:04
tags: vercial-align(图片与span竖直居中)
categories: 
- web前端css
---
#vercial-align如何让图片和span在div中居中
```
HTML5
    <div>
        <img src="">
        <span>文字</span>
    </div>
```
```
css样式
    div{
        height:200px;
        width:300px;
    }
    img{
        vercial-align:middle;
    }
    span{
        line-height:200px;
    }
```

# 文字出现浮动的情况,图片竖直方向居中 （浮动》脱离布局流）
```
<div style="height:40px;">
    <div style="float:left;">
        <img style="vertical-align:middle;" src="">
        <span style="line-height:40px;"></span>
    </div> 
    <span style="float:right; line-height:40px;"></span>   
    <div style="clear:both"></div> 
</div> 
```