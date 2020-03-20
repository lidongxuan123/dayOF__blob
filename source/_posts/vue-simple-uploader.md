---
title: vue-simple-uploader 文件上传(断点·秒传·md5计算)
date: 2020-03-05 11:35:16
tags: vue-simple-uploader 文件上传(断点·秒传·md5计算)
categories: 
- npm包知识
---

# 文件上传组件vue-simple-uploader
## 什么是vue-simple-uploader
> 详细了解: [vue-simple-uploader](https://www.cnblogs.com/xiahj/p/vue-simple-uploader.html)
> 断点续传[断点续传](https://blog.csdn.net/tangcc110/article/details/85226045)
## 安装使用
npm install vue-simple-uploader --save
import uploader from 'vue-simple-uploader'
Vue.use(uploader)

## vue-simple-uploader参数解释
```
<uploader
    ref="uploader"
    :options="options"
    :autoStart="false"
    @file-added="onFileAdded"
    @file-success="onFileSuccess"
    @file-progress="onFileProgress"
    @file-error="onFileError"
    class="uploader-app">
    
<uploader-btn id="global-uploader-btn" :attrs="attrs" ref="uploadBtn">选择文件</uploader-btn>
```
> options: 为文件的配置文件
> file-added: 文件添加的时候方法
> file-success: 文件发送成功的时候执行
> file-progerss: 文件显示进度条
> file-error: 上传文件失败
> options里的参数：
```
options: {
    target: http://127.0.0.1:8080/api/send/files, 目标地址
    chunkSize: "2048",  分块大小
    fileParameterName: "file",   默认文件名
    maxChunkReteries: 3,   重试次数
    testChunks: true,  是否开启服务器分片校验
    <!--服务器分片校验函数，秒传及断点续传基础-->
    <!--在文件上传的时候会首先发送一个get请求，然后是post请求,发送文件数据-->
    <!--message和chunk是发送get请求后返回的数据，可以根据这两个值来判断秒传和断点续传，-->
    checkChunkUploadedByResponse: function(chunk, message){
        let objMessage = JSON.parse(message)
        if(objMessage.skipUpload) {
            return true
        }
        return (objMessage.uploaded || []).indexOf(chunk.offset + 1) >= 0
    }
}
attrs: {
         // 接受的文件类型，形如['.png', '.jpg', '.jpeg', '.gif', '.bmp'...] 这里我封装了一下
            accept: ACCEPT_CONFIG.getAll()
        },
panelShow: false,   //选择文件后，展示上传panel
```
## 相关的方法
1. upload() 开始或者继续上传
2. pause() 暂停上传
3. resume() 继续上传
4. cancel() 取消所有上传文件
5. progerss() 返回一个0-1的浮点数
6. isuploading()返回一个布尔值

## 文件上传时候如何计算MD5
> 断点续传及秒传的基础是要计算文件的MD5，这是文件的唯一标识，然后服务器根据MD5进行判断，是进行秒传还是断点续传
> 在file-added事件之后就计算MD5
> 加密工具spark-md5  安装方式：npm install spark-md5 --save
> file有个属性是uniqueIdentifier，代表文件的唯一标识，把计算出的md5赋值给这个属性 file.uniqueIdentifier = md5

## 计算MD5的时候需要掌握的基础知识
1. let fileReader = new FileReader()
2. File.prototype.slice  || File.prototype.mozSlice || File.prototype.webkitSlice
3. new SparkMD5.ArrayBuffer()
4. fileReader.onload = function(){

}
5. spark.append()
6. spark.end()
7. fileReader.onerror = function() {
    
}
8. fileReader.readAsArrayBuffer()
###断点续传和秒传
> 每次上传最开始，vue-simple-uploader会发送一个get请求，来问服务器哪些片段已经上传过。
checkChunkUploadedByResponse: function (chunk, message) {
     let objMessage = JSON.parse(message);
     if (objMessage.skipUpload) {
         return true;
     }

     return (objMessage.uploaded || []).indexOf(chunk.offset + 1) >= 0
},



### 其他涉及到的知识点
1. new FileReader() [文件操作](https://www.cnblogs.com/xzybk/p/11593269.html)
2. input文件选择框,进行文件的选择[文件选择](https://developer.mozilla.org/zh-CN/docs/Web/API/File/Using_files_from_web_applications)
> readAsBinaryString  该方法将文件读取为二进制字符串，通常我们将它传送到后端，后端通过这段字符串存储文件
> readAsDataURL:该方法将文件读取为一段以data:开头的字符串，这段字符串的实质是Data URL, DataURL是一种将小文件直接嵌入文档的方案，这种小文件按通常指的是
> readAsText: 将文本读取为文本
处理事件： onabort：中断时触发
          onerror：出错时触发
          onload：文件读取成功完成时触发
          onloadend：读取完成时触发，无论成功或失败
          onloadstart：读取开始时触发
          onprogress：读取中
> spark-md5.js (用于计算MD5)
1. sparkMD5.hashBinary()直接将整个文件的二进制码传入，直接返回文件的md5，这种方法对于小文件会比较有优势
2. 另一种方法利用js中file对象的slice方法，将文件分片后逐个输入spark.appendBinary()方法来计算，最后通过spark.end()方法输出结果，可以计算进度信息。


### 项目源码
```
<template>
  <div>
    <uploader :options="options" :autoStart="false" :file-status-text="statusText" class="uploader-example" ref="uploader" @file-complete="fileComplete"
      @file-added="onFileAdded" @file-success="onFileSuccess" @file-error="onFileError" @complete="complete"></uploader>
  </div>
</template>

<script>
  import SparkMD5 from 'spark-md5'
  export default {
    data() {
      return {
        options: {
          target: 'http://127.0.0.1:8080/api/send/files', // '//jsonplaceholder.typicode.com/posts/',
          testChunks: true,
          // get请求
          checkChunkUploadedByResponse: function (chunk, message) {
         
            var objMessage = {}
            objMessage = JSON.parse(message)
            // 妙传
            if(objMessage.code == 0) {
              return true
            } else if (objMessage.uploaded_chunks > 0) {
              return (objMessage.uploaded_chunks || []).indexOf(chunk.offset + 1) >= 0
            } else {
              return false
            }
            // try {
            //   objMessage = JSON.parse(message)
            // } catch (e) { }
            // return (objMessage.uploaded_chunks || []).indexOf(chunk.offset + 1) >= 0
          }
        },
        attrs: {
          accept: 'image/*'
        },
        statusText: {
          success: '成功了',
          error: '出错了',
          uploading: '上传中',
          paused: '暂停中',
          waiting: '等待中'
        }
      }
    },
    methods: {
      onFileSuccess(rootFile, file, response) {
        console.log("------------------------")
        console.log(rootFile)
        console.log(file)
        console.log(response)
        console.log("-------------------------")
      },
      onFileError() {
        // alert("文件上传失败")
      },
      // 添加文件的时候
      onFileAdded(file) {
        // 添加文件的时候先进行md5的计算
        console.log("添加文件")
        this.computeMD5(file)
      },
      // 计算md5
      computeMD5(file) {
        let fileReader = new FileReader();
        let time = new Date().getTime();
        let blobSlice = File.prototype.slice || File.prototype.mozSlice || File.prototype.webkitSlice;
        let currentChunk = 0;
        const chunkSize = 10 * 1024 * 1000;
        let chunks = Math.ceil(file.size / chunkSize);
        let spark = new SparkMD5.ArrayBuffer();
        file.pause();
        loadNext();
        fileReader.onload = (e => {
          console.log(e.target.result)
          spark.append(e.target.result);
          if (currentChunk < chunks) {
            currentChunk++;
            loadNext();
            // 实时展示MD5的计算进度
          } else {
            let md5 = spark.end();
            this.computeMD5Success(md5, file);
            console.log(`MD5计算完毕：${file.name} \nMD5：${md5} \n分片：${chunks} 大小:${file.size} 用时：${new Date().getTime() - time} ms`);
          }
        });
        fileReader.onerror = function () {
          this.error(`文件${file.name}读取出错，请检查该文件`)
          file.cancel();
        };
        function loadNext() {
          let start = currentChunk * chunkSize;
          let end = ((start + chunkSize) >= file.size) ? file.size : start + chunkSize;
          fileReader.readAsArrayBuffer(blobSlice.call(file.file, start, end));
        }
      },
      computeMD5Success(md5, file) {
        file.uniqueIdentifier = md5;
        file.pause();
        file.resume();
      },
      complete() {
        console.log('complete', arguments)
      },
      fileComplete() {
        console.log('file complete', arguments)
      }
    },
    mounted() {
      console.log(this.$refs.uploader.uploader)
      this.$nextTick(() => {
        window.uploader = this.$refs.uploader.uploader
      })
    }
  }

</script>

<style>
  .uploader-example {
    width: 880px;
    padding: 15px;
    margin: 40px auto 0;
    font-size: 12px;
    box-shadow: 0 0 10px rgba(0, 0, 0, .4);
  }

  .uploader-example .uploader-btn {
    margin-right: 4px;
  }

  .uploader-example .uploader-list {
    max-height: 440px;
    overflow: auto;
    overflow-x: hidden;
    overflow-y: auto;
  }
</style>
```
####node后端
```
var express = require('express');
var router = express.Router();
var multer = require('multer');
var upload = multer({ dest: 'upload/' }).any();
var fs = require("fs")
/* GET home page. */
router.get('/', function (req, res, next) {
  res.render('index', { title: 'Express' });
});
router.get("/user", function (req, res) {
  console.log("user")
  res.send("user")
})
router.get("/send/files", function (req, res) {
  res.send({
    code: 0,
    msg:"这是get请求",
    data:[],
    uploaded_chunks:[1,2,3,4]
  })
})
// 80186ed5cb2e98d5cb4b7e4e2e35618d  图片上传的md5
router.post("/send/files", function (req, res) {
    // 不存在MD5表示文件没有上传
    upload(req, res, function (err) {
    console.log("post-----------")
      if (err) {
        console.log(err);
        return;
      }
      req.file = req.files[0];
      var tmp_path = req.file.path;
      var target_path = 'uploads/' + req.file.originalname;
      if (!fs.existsSync('uploads/')) {
        fs.mkdirSync('uploads/');
      }
      var src = fs.createReadStream(tmp_path);
      var dest = fs.createWriteStream(target_path);
      src.pipe(dest);
      src.on('end', function () {
        res.send({
          code: 0,
          msg: "文件上传成功",
          data: []
        });
      });
      src.on('error', function (err) {
        res.end();
        console.log(err);
      });
    });
})
module.exports = router;

```