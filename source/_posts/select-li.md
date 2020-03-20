---
title: 导航条
date: 2020-03-19 09:03:17
tags: 导航条
categories:
- web前端css
---
# 导航条
 
```
 <style>
    ul {
        height: 40px;
        list-style: none;
        margin:0;
        padding: 0;
        font-size:0;
    }
    li {
        display: inline-block;
        height: 40px;
        width:80px;
        background: lightblue;
        position: relative;
    }
    a {
        text-decoration: none;
        display: block;
        height: inherit;
        line-height: 40px;
        font-size:14px;
        text-align: center
    }
    .li_div{
        position: absolute;
        left: 0;
        line-height: 25px;
        background: gray;
    }
    p{
        padding: 0;
        margin: 0;
    }
    </style>

     <ul>
       <li>
           <a href="">百度</a>
           <div class="li_div">
               <p>百度翻译</p>
               <p>百度图表</p>
               <p>百度地图</p>
           </div>
        </li>
       <li><a href="">搜狐</a></li>
       <li><a href="">360</a></li>
   </ul>
```