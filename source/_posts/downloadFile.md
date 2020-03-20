---
title: 前端项目实现文件的下载downloadFile
date: 2019-11-22 10:14:34
tags: 前端项目实现文件的下载downloadFile
categories: 
- JavaScript
---

# 文件下载
1. a标签的下载方式
```
<a href="下载的url / 文件地址">下载</a>
```
2. window.location.href = "下载的url"
> 地址url为下载路径，则进行下载
> 地址为地址路径，则进行跳转
```
window.loaction.href= "下载url"
```
3. window.open = "下载的url"
4. 使用<a>标签下载
```
<a href="/api/download/test">下载</a>

*后台*
app.get("/download/test",function(req,res) {
    fs.readFile(__dirname+'/文件名', "utf-8", function(err,data) {
        if (err) {
            console.log(err)
        } else {
            res.send(data)
        }
    })
})

```
5. 下载后台写法
```
app.get("/download/test",function(req,res) {
    res.download(path.resolve(__dirname+"/111/txt"))
})
```
6. 文件下载 [文件下载第六种方式](https://www.jianshu.com/p/917a15445510)

```
jquery的下载方式

$ajax({
    url: url,
    type: "post",
    data: data,
    success: function(res) {
        let content = res.data
        const blob = new Blob([data])
        let filename ="filename.txt"
        if ("download" in document.createElement("a)) {
            const fileLink = document.createElement("a")
            fileLink.download = filename
            fileLink.style.display = "none"
            fileLink.href = URL.createObjectURL(blob)
            document.body.appendChild(fileLink)
            fileLink.click()
            URL.revokeObjectURL(fileLink.href)
            document.body.removeChild(fileLink)
        } else {
            nabigator.msSaveBlob(blob,filename)
        }
    }
})
```
</style>   

