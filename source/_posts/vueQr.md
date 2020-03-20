---
title: vueQr 生成二维码
date: 2020-01-08 09:33:55
tags: 生成需要的二维码
categories: 
- npm包知识
---

# 生成二维码
1. 组件化模式生成二维码
```
// 包名： vue-qr
import VueQr from 'vue-qr'
Vue.component('VueQr', VueQr)

<vue-qr text="Hello world!" :callback="test" qid="testid"></vue-qr>
```
2. DOM方式生成二维码
```
// 包名： QRCode
<div id="qrcode"></div>

import QRCode from "qrcodejs2"

qrcode() {
    let that = this;
    let qrcode = new QRCode('qrcode', {
        width: 124,
        height: 124,        // 高度
        text: "https://www.baidu.com",   // 二维码内容
        // render: 'canvas' ,   // 设置渲染方式（有两种方式 table和canvas，默认是canvas）
        // background: '#f0f',   // 背景色
        // foreground: '#333'    // 前景色
    })
}
```

