---
title: clipboard 拷贝文字
date: 2020-01-08 09:53:37
tags: clipboard 拷贝文字
categories: 
- npm包知识
---
# 连接地址
[clipboard 拷贝文字](http://www.clipboardjs.cn/)
# 安装
> npm install clipboard --save

```
 <div>
    今天是个好日子
    <button class="btn" id="copy" @click="copy" data-clipboard-text="Just because you can doesn't mean you should — clipboard.js">复制</button>
</div>
  import ClipboardJS  from 'clipboard'
  components: {
    ClipboardJS
    },
    copy() {
        var clipboard = new ClipboardJS('.btn');

        clipboard.on('success', function (e) {
          alert('success')
          e.clearSelection();
        });
        clipboard.on('error', function (e) {
          console.error('Action:', e.action);
          alert('error')
          console.error('Trigger:', e.trigger);
        });
      },
```