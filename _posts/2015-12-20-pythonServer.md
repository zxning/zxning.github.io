---
layout: post
title: 使用python搭建临时server并访问一个接口
categories: [Python]
description: some word here
keywords: keyword1, keyword2
---

### 问题描述
最近需要对外演示fiddler的TextWizard功能，因此，需要访问一个接口，而且希望里面接口的返回值里面有encode过的内容。为了避嫌，不想使用项目上正在使用的接口，因此，打算自己写一个，根据这个需求，需要做两件事情

1. 有个服务器供我放这个接口
2. 有个json文件

### 服务器的解决办法

1.  使用现成的测试服务器
    - 结论:下下方案，实在不行的时候再用现成的，因为测试服务器是已经配置好的，可以直接用， 但是根本不知道配置了什么，怎么配置的
2. 有Linux虚机，自己搭一个服务器
    - 结论：在一台服务器上放置了json文件后，访问不到，后来了解到是跨域的原因，需要在该服务器上安装xampp重新配置环境，先记个ToDo吧
3. 曾经有个大神跟我说可以使用python临时在本机搭一个，只需要使用一句命令即可  
**具体操作：**

- 在某路径下启动cmd，运行如下命令
- 将json文件放到该目录下
- 在浏览器中访问这个接口：http://localhost:8081/JsonTes.json

```
python  -m SimpleHTTPServer 8081
```
*注：其中8081是端口号，可以自己进行设置*


### json文件
仿照服务器上的json文件写了一个，如下：


```
{
	"roommate": [{
		"photo": "https%3A%2F%2Fencrypted-tbn2.gstatic.com%2Fimages%3Fq%3Dtbn%3AANd9GcQfkJ91eZhts0Y-nYFa8HpMwldZoBJ43hdpatT_FRGTCPRtnTHv",
		"name": "%E5%B1%B1%E5%8F%A3%E7%99%BE%E6%83%A0",
		"id": "0000000",
		"company": "%E5%8C%97%E4%BA%AC%E6%90%9C%E7%8B%97%E7%A7%91%E6%8A%80%E5%8F%91%E5%B1%95%E6%9C%89%E9%99%90%E5%85%AC%E5%8F%B8",
		"age": "30",
		"birthday": "19900909",
		"tip": "%E6%90%9C%E7%8B%97%E8%BE%93%E5%85%A5%E6%B3%95",  
		"brief": "%E6%90%9C%E7%8B%97%E5%8E%9F%E5%88%9B%E8%A1%A8%E6%83%85%E8%AE%BE%E8%AE%A1%E5%A4%A7%E8%B5%9B",
		"description": "%E6%90%9C%E7%8B%97%E5%8E%9F%E5%88%9B%E8%A1%A8%E6%83%85%E8%AE%BE%E8%AE%A1%E5%A4%A7%E8%B5%9B",
		"size": "11.65%20MB",
		"date": "2015-01-22%2015%3A55%3A55",
		"date_added": "2013-01-14%2010%3A01%3A26",
		"score": "100",
		"url": "http%3A%2F%2Fmobile.zhushou.sogou.com%2Fandroid%2Fdownload.html%3Fapp_id%3D35214%26data_id%3D2",
		"md5": "1fe81752ee51b6ddbbd5daafbff3a049",
		"group_name": "%E5%BA%94%E7%94%A8",
		"category_name": "%E9%82%AE%E7%AE%B1"
	}],
	"dormmate": [{
		"photo": "https%3A%2F%2Fencrypted-tbn2.gstatic.com%2Fimages%3Fq%3Dtbn%3AANd9GcQfkJ91eZhts0Y-nYFa8HpMwldZoBJ43hdpatT_FRGTCPRtnTHv",
		"name": "%E5%B1%B1%E5%8F%A3%E7%99%BE%E6%83%A0",
		"id": "0000000",
		"company": "%E5%8C%97%E4%BA%AC%E6%90%9C%E7%8B%97%E7%A7%91%E6%8A%80%E5%8F%91%E5%B1%95%E6%9C%89%E9%99%90%E5%85%AC%E5%8F%B8",
		"age": "30",
		"birthday": "19900909",
		"tip": "%E6%90%9C%E7%8B%97%E8%BE%93%E5%85%A5%E6%B3%95",  
		"brief": "%E6%90%9C%E7%8B%97%E5%8E%9F%E5%88%9B%E8%A1%A8%E6%83%85%E8%AE%BE%E8%AE%A1%E5%A4%A7%E8%B5%9B",
		"description": "%E6%90%9C%E7%8B%97%E5%8E%9F%E5%88%9B%E8%A1%A8%E6%83%85%E8%AE%BE%E8%AE%A1%E5%A4%A7%E8%B5%9B",
		"size": "11.65%20MB",
		"date": "2015-01-22%2015%3A55%3A55",
		"date_added": "2013-01-14%2010%3A01%3A26",
		"score": "100",
		"url": "http%3A%2F%2Fmobile.zhushou.sogou.com%2Fandroid%2Fdownload.html%3Fapp_id%3D35214%26data_id%3D2",
		"md5": "1fe81752ee51b6ddbbd5daafbff3a049",
		"group_name": "%E5%BA%94%E7%94%A8",
		"category_name": "%E9%82%AE%E7%AE%B1"
    }]
}
```

### 遇到的问题
在浏览器中输入http://localhost:8081/JsonTest.json回车后，浏览器直接将json下载，而不是直接展示在浏览器里。为了解决这个问题，请教了一同事后，发现，只要将后缀改成json替换成HTML则可以解决这个问题

