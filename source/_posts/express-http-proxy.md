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
[express-http-proxy](https://www.jianshu.com/p/846e8b555ead)

```
express-http-proxy
let proxyConfig = {
    URL: "XXXXXX"
    PORT: "XXX"
} 
```
1. forwardPath: 选项用于在代理请求之前修改路径
```
var proxy = require('express-http-proxy'); 
var app = require('express')(); 
app.use('/proxy', proxy('www.google.com', {
  forwardPath: function(req, res) {
    return require('url').parse(req.url).path;
  }
}));
```
2. forwardPathAsync: 在发送代理请求之前，使用promise异步请求修改路径
```
app.use(proxy('httpbin.org', {
  forwardPathAsync: function() {
    return new Promise(function(resolve, reject) {
      // ... 
      // eventually 
      resolve( /* your resolved forwardPath as string */ )
    });
  }
}));
```
3. filter选项用于筛选哪些请求可以被代理转发
```
app.use('/proxy', proxy('www.google.com', {
  filter: function(req, res) {
     return req.method == 'GET';
  },
  forwardPath: function(req, res) {
    return require('url').parse(req.url).path;
  }
}));
```
4. intercept 选项用于在将响应返回客户端之前对响应做处理
```
app.use('/proxy', proxy('www.google.com', {
  intercept: function(rsp, data, req, res, callback) {
    // rsp - original response from the target 
    data = JSON.parse(data.toString('utf8'));
    callback(null, JSON.stringify(data));
  }
}));
```
5. decorateRequest 与intercept相反，decorateRequest选项用于在请求通过代理转发至目标主机之前，对请求进行处理
6. https通常代理请求的协议类型与原始请求保持一致，如果代理请求需要用https协议，可以用https选项强制实现
```
app.use('/proxy', proxy('www.google.com', {
  https: true
}));
```
7. preserveHostHdr将HTTP头部复制到express代理服务器的HTTP头部
```
app.use('/proxy', proxy('www.google.com', {
  preserveHostHdr: true
}));
```
8. reqAsBuffer 请求体（req.body）编码为Node Buffer
```
app.use('/proxy', proxy('www.google.com', {
  reqAsBuffer: true
}));
```
9. reqBodyEncoding 编码格式
request body默认编码格式为 utf-8。
当代理请求体为Buffer时，使用null来保存缓冲(例如，图像上传) ，接受 raw-body支持的任何值。
编码格式也可以通过intercept选项实现
```
app.use('/post', proxy('httpbin.org', {
  reqBodyEncoding: null
}));
```
10. timeout增加超时
默认情况下。node在连接过程中，是没有timeout的。使用timeout选项增加超时，Timed-out requests 将会返回504和X-Timeout-Reason header。
```
app.use('/', proxy('httpbin.org', {
  timeout: 2000  // in milliseconds, two seconds 
}));
```

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