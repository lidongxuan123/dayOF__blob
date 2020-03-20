---
title: 两个div同时增长 flex-grow (height和宽度)
date: 2020-03-19 17:31:20
tags: 两个div同时增长 flex-grow
categories: 
- web前端css
---

# 使用display:flex;做到同时增长
```
    <style>
        .div_out {
            display: flex;
        }
        .div_1 {
            width: 0;
            flex-grow: 1;
            background: lightcoral;
        }
        .div_2 {
            width: 0;
            flex-grow: 1;
            background: lightgray;
        }
    </style>
    <div class="div_out">
        <div class="div_1">
            <p>1111111</p>
            <p>1111111</p>
            <p>1111111</p>
            <p>1111111</p>
        </div>
        <div class="div_2">
            <p>1111111</p>
        </div>
    </div>
```
