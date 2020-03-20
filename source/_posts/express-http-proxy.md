---
title: 服务器代理express-http-proxy
date: 2019-12-16 14:24:01
tags: 服务器代理
categories: 
- npm包知识
---
# 自己对跨域的理解
> 浏览器跨域是对数据的请求。前端接口 --- 中间层 --- 后台管理，其中前端只是发送请求，通过中间层跨域，从而访问后台的接口
[跨域知识](https://cloud.tencent.com/developer/ask/37177)
[什么是跨域](https://blog.csdn.net/weixin_40597676/article/details/78791590)
# 使用方法1：
```
var httpProxy = require('http-proxy');
var proxy = httpProxy.createProxyServer();
router.use('*', function (req, res) {
    proxy.web(req, res, { target: 'http://127.0.0.1:8888', changeOrigin: true, secure: false });
});
```
# 使用方法2：
[代理的使用方法实例，解决http-proxy-middleware不能用的原因](https://blog.csdn.net/lin819397746/article/details/96107376)
代理中加上解析后body数据在转回来即可
```
    const proxy = require('http-proxy-middleware');
    var restream = function(proxyReq, req, res, options) {
        if (req.body) {
           let bodyData = JSON.stringify(req.body);
           // incase if content-type is application/x-www-form-urlencoded -> we need to change to application/json
           proxyReq.setHeader('Content-Type','application/json');
           proxyReq.setHeader('Content-Length', Buffer.byteLength(bodyData));
           // stream the content
            proxyReq.write(bodyData);
        }
    }
    var apiProxy = proxy('/api', {
    target: 'https://xxx.xxx.xxx.xxx',
    secure: false,
    changeOrigin: true,
    onProxyReq: restream
    });
    app.use(apiProxy);
```


# 使用方法3：
```
const proxy = require('express-http-proxy')
let opts = {
    preserveHostHdr: true,
    reqAsBuffer: true,
     //转发之前触发该方法
     proxyReqPathResolver: function(req, res) {
        //这个代理会把匹配到的url（下面的 ‘/api’等）去掉，转发过去直接404，这里手动加回来，
        req.url = req.baseUrl+req.url;
        return require('url').parse(req.url).path;
    },
}
app.use('/api',proxy('https://xxx.xxx.xxx.xxx',opts));
```

# 为啥使用这个,而不选择下面两个
> http-proxy  http-proxy-middleware
1. 问题原因： 使用上面两个get请求的代理正常，post请求的代理没有反应
2. 上面这两种出现的情况是：
```
[HPM] Proxy created: /  -> http://127.0.0.1:4000/api/send/username
[HPM] Proxy created: /  -> http://127.0.0.1:4000/api/send/username
```