---
title: TLS描述信息
date: 2020-04-23 11:10:05
tags: TLS描述信息
categories: 
- 详细知识点
---

# TLS
> 介绍: 安全传输层协议(TLS)用于在两个通信应用程序之间提供保密性和数据完整性, 协议由两层组成: tls记录协议和TLS握手协议

> 简称: 传输层安全性协议(TSL),及其前身安全套接层SSL是一种安全协议,目的是为互联网通信提供安全及数据完整性保障.

1. tls安全传输层
const tls = require("tls")
2. tls/ssl概念
tls/ssl是公共/私人的密钥基础设施. 私钥生成方式:用OpenSSL的命令行来生成一个2048位的RSA私钥
私钥: openssl genrsa -out ryans-key.pem 2048
CSR文件(根据私钥生成一个证书申请文件): openssl req -new -sha256 -key ryans-key.pem -out ryans-csr.pem
证书: openssl x509 -req -in ryans-csr.pem -signkey ryans-key.pem -out ryans-cert.pem
证书生成以后又可以用来生成一个.pfx或者.p12文件
openssl pkcs12 -export -in ryans-cert.pem -inkey ryans-key.pem \
      -certfile ca-cert.pem -out ryans.pfx

3. 完全前向保密
密钥协商的方法,客户端和服务端会临时生成的密钥进行对称加密的密钥交换,即使服务器端私钥发生泄漏,也无法获取全部内容
目前常用的前向保密: DHE ECDHE 
使用DHE算法 OpenSSL 命令生成参数:
openssl dhparam -outform PEM -out dhparam.pem 2048
4. ALPN 和 SNI 
ALPN: 应用层协议协商扩展  允许将一个TLS服务用于多种协议(HTTTP \HTTP2)
SNI: 服务器名称指示 允许一个TLS服务器用于具有不同SSL证书的多个主机名
5. 与共享的密钥(不解)
6. 客户端发起的重协商攻击缓解
tLS协议允许刻划断在TLS会话中进行重协商,协商会消耗大量的资源,将导致服务器存在潜在的被DDOS攻击的可能.
tls.CLIENT_RENEG_LIMIT <number> 指定重协商请求的次数限制，默认为 3。
tls.CLIENT_RENEG_WINDOW <number> 指定限制次数的生效时间段，默认为 600（10 分钟）。
7. 会话恢复
TLS建立连接比较慢,可以通过重用绘画状态
会话标识符服务器为新连接生成唯一的ID并将其发送到客户机。客户端和服务器保存会话状态。当重新连接时，客户端发送他们保存的会话状态的ID，如果服务器也有该ID的状态，它可以同意使用它。否则，服务器将创建一个新会话
8. TLS的使用
const tls = require("tls")
const fs = require("fs")
const options = {
    key: fs.readFileSync("")
    cert: fs.readFileSync(""),
    ca: [fs.readFileSync("server-cert.pem")],
    checkServerIdentity: () => {
        return null
    }
}
const socket  = tls.connect(port, options, () => {
    console.log()
    process.stdin.pipe()
    process.stdin.resume()
    socket.setEncoding("utf8)
    socket.on('data', (data)=> {

    })
    socket.on('end', () => {
        
    })
})


