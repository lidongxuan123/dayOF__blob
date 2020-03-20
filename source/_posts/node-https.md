---
title: node_https  https配置
date: 2020-03-09 10:49:38
tags: https的配置
categories: 
- npm包知识
---
# https详细介绍
```
var Option = {
key: fs.readFileSync('./li/server.key'),  //私钥
ca: fs.readFileSync('./li/server.csr'),  //公钥
cert: fs.readFileSync('./li/server.crt') //证书
}
var appserver = https.createServer(Option, app)
appserver.listen(3000,function(){
  console.log("服务启动成功")
})
module.exports = app;
```
> [https详细介绍](https://mp.weixin.qq.com/s/ibwNtDc2zd2tdhMN7iROJw)

##https概念知识
> 是以安全为目标的 HTTP 通道，在HTTP的基础上通过传输加密和身份认证保证了传输过程的安全性 [1]  。HTTPS 在HTTP 的基础下加入SSL 层，HTTPS 的安全基础是 SSL，因此加密的详细内容就需要 SSL。 HTTPS 存在不同于 HTTP 的默认端口及一个加密/身份验证层（在 HTTP与 TCP 之间）。这个系统提供了身份验证与加密通讯方法

##TLS/SSL概念知识
地址：[TLS/SSL](https://www.ctolib.com/docs-nodejs-c-tls.html)

##TLS里的配置参数
> tls模块使用openSSL来提供传输层安全性和安全套接层
> TLS/SSL时一种公钥/私钥基础架构，每个客户端和服务端都需要私钥
1. 私钥的创建方法
openssl genrsa -out ryans-key.pem 2048
>

2. 参数介绍
> pfx: 包含私钥，证书和服务器的 CA 证书（PFX 或 PKCS12 格式）字符串或缓存Buffer。（key, cert 和 ca互斥）。
> key: 包含服务器私钥（PEM 格式）字符串或缓存Buffer。（可以是keys的数组）（必传）
> passphrase: 私钥或 pfx 的密码字符串
> cert: 包含服务器证书key（PEM 格式）字符串或缓存Buffer。（可以是certs的数组）（必传）。
> ca: 信任的证书（PEM 格式）的字符串/缓存数组。如果忽略这个参数，将会使用"root" CAs ，比如 VeriSign。用来授权连接。
> crl : 不是 PEM 编码 CRLs （证书撤销列表 Certificate Revocation List）的字符串就是字符串列表.
> ciphers: 要使用或排除的密码（cipher）字符串
> ecdhCurve: 包含用来 ECDH 秘钥交换弧形（curve）名字符串，或者 false 禁用 ECDH。
> dhparam: DH 参数文件，用于 DHE 秘钥协商。使用 openssl dhparam 命令来创建。如果加载文件失败，会悄悄的抛弃它。
> handshakeTimeout: 如果 SSL/TLS 握手事件超过这个参数，会放弃里连接。 默认是 120 秒.握手超时后， tls.Server 对象会触发 'clientError' 事件。
> requestCert: 如果设为 true，服务器会要求连接的客户端发送证书，并尝试验证证书。默认：false。
> rejectUnauthorized: 如果为 true ，服务器将会拒绝任何不被 CAs 列表授权的连接。仅 requestCert 参数为 true 时这个参数才有效。默认： false。
> checkServerIdentity(servername, cert): 提供一个重写的方法来检查证书对应的主机名。如果验证失败，返回 error。如果验证通过，返回 undefined 。
> sessionTimeout: 整数，设定了服务器创建TLS 会话标示符（TLS session identifiers）和 TLS 会话票据（TLS session tickets）后的超时时间（单位：秒）。更多细节参见：SSL_CTX_set_timeout。
> secureProtocol: SSL 使用的方法，例如，SSLv3_method 强制 SSL 版本为3。可能的值定义于你所安装的 OpenSSL 中的常量SSL_METHODS。
> secureOptions: 设置服务器配置。例如设置 SSL_OP_NO_SSLv3 可用禁用 SSLv3 协议。所有可用的参数见SSL_CTX_set_options
> 
> 
> 
> 
> 
