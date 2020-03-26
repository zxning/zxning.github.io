---
layout: post
title: postman抓HTTPS的包
categories: [interface]
description: some word here
keywords: keyword1, keyword2
---

postman可以作为proxy抓获手机端的HTTP，HTTPS请求，这样获取的请求就可以直接用，有很多参数就不用手动输入了。获取HTTP操作方式如下：

### 一、抓手机端的HTTP

1. 点击右上角的卫星图标 > capture requests ,打开开关

![](/images/2020-03-26-1-1.png)

2. 在手机端设置代理IP和端口号，注意：postman的默认端口号是5555

![](/images/2020-03-26-1.png)

3. 然后再在手机端使用APP，会直接将请求显示在History的tab上


### 二、抓手机端的HTTPS

在上面问题的基础上继续抓HTTPS

1. 页面右上角的扳手图标 > seeting > General, 关闭SSL选项，如图所示：

![](/images/2020-03-26-2.png)

2. 继续上面的步骤，切换到Cerficates 的tab上，点击Add cerficate,如下图

![](/images/2020-03-26-2.png)

网上大部分的方法都是说自己生成证书然后上传，试过后发现并不能用，终于有个人说可以用Charles的公钥，私钥，说的很有道理，果然可以。将Charles导出的文件分别上传到postman的对应位置，域名随便填写的m.baidu.com。注意：不要写自己将要自己的域名，会通不过

![](/images/2020-03-26-4.png)

![](/images/2020-03-26-3.png)


### 三、使用postman测试HTTPS

需要做问题二的设置，要不然会出现如下所示的错误：

![](/images/2020-03-26-5.png)
