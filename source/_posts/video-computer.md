---
title: HTML5调用电脑的摄像头从而实现直播软件的开发
date: 2020-04-07 17:23:37
tags: HTML5调用电脑的摄像头从而实现直播软件的开发
categories: 
- JavaScript
---

# 使用HTML5/Javascript调用PC端摄像头
```
let video = document.getElementById("video")
console.log(window.navigator.mediaDevices)
let constraints = {
    // 宽高500表示使用的分辨率
    video: { width: 500, height: 500 },
    audio: true
};
let promise = navigator.mediaDevices.getUserMedia(constraints);
promise.then(function (MediaStream) {
    console.log(MediaStream)
    video.srcObject = MediaStream;
    video.play();

    <!--每隔1s打印数据-->
    let mediaRecorder = new MediaRecorder(MediaStream);
    mediaRecorder.ondataavailable = function (blob) {
    console.log(blob.data)
    }
    mediaRecorder.start(1000)
}).catch(function (PermissionDeniedError) {
    console.log(PermissionDeniedError);
})
```