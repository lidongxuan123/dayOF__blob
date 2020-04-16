---
title: vue项目中使用sockte.io
date: 2020-04-15 15:53:38
tags: vue项目中使用sockte.io
categories: 
- npm包知识
---

# Vue-sockte.io 和sockte.io的使用
1. Vue-sockte.io (vue中使用)
```
import Vue from 'vue'
  import VueSocketIO from 'vue-socket.io'
  import socketio from 'socket.io-client';
  Vue.use(new VueSocketIO({
    debug: true,
    // 服务器端地址
    connection: socketio('http://127.0.0.1:3000/test'),

  }))
  export default {
    data() {
        return {

        }
    },
    sockets: {

    },
    methods: {
        func(){
            this.$socket.emit()
            this.$socket.on()
        }
    }
  }
```
2. sockte.io (服务端的使用方式)

```
var io = require('socket.io').listen(server);
<!--配置源地址,防止其他人进行跨域连接-->
io.origins((origin, callback) => {
  if (origin !== 'http://127.0.0.1:8080') {
    return callback('origin not allowed', false);
  }
  callback(null, true);
});

io.of('/test').on("connect", function (socket) {
  socket.on("firstEnter",function(data) {
    socket.id = data.id
    socket.name = data.name
    socket.remoteId = data.remoteId
    group.push(socket)
  }) 
  socket.on("single", function(data) {
    <!--群发-->
    // socket.broadcast.emit("single", data);
    console.log(data.remoteId)
    if(group.length > 0) {
      group.forEach(function(element, index) {
        if (element.id == data.remoteId) {
            <!--发给单个人-->
           element.emit("single","wwww")
        }
      })
    }
  })
})
```

# socket.io 事件速查表
1. 连接
io.on("connect", function(socket))
2. 发送给当前客户端
socket.emit("事件", "返回值")
3. 发送给所有的客户端，除了发送者
socket.broadcast.emit("事件","内容")
4. 发送给同在game房间的所有客户端，除了发送者
socket.to("game").emit("事件", "参数")
5. 发送给同在game1或game2房间的所有用户
socket.to('game1').to('game2').emit('nice game', "let's play a game (too)");
6. 发送给同在 'game' 房间的所有客户端，包括发送者
  io.in('game').emit('big-announcement', 'the game will start soon');
7. 发送给指定 socketid 的客户端（私密消息）
  socket.to(<socketid>).emit('hey', 'I just met you');
8.  包含回执的消息
  socket.emit('question', 'do you think so?', function (answer) {});
9. 不压缩，直接发送
   socket.compress(false).emit('uncompressed', "that's rough");
10. 如果客户端还不能接收消息，那么消息可能丢失
  socket.volatile.emit('maybe', 'do you really need it?');
11. 发送给当前 node 实例下的所有客户端（在使用多个 node 实例的情况下）
  io.local.emit('hi', 'my lovely babies');







