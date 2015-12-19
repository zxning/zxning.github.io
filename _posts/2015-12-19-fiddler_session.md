---
layout: post
title: Fiddler|session的含义
categories: [测试工具]
description: some word here
keywords: keyword1, keyword2
---

### 概述
Fiddler 的 session 都是按照顺序展示的，在序号前面则是 session 的快捷图标，如下图所示：


![2015-12-19-1](/images/2015-12-19-1.png)

### session图标
1. ![2015-12-19-2](/images/2015-12-19-2.png) session被客户端应用，Fiddler或服务器中止。


例如：当我打开一个网页后，网页的response还没有发送完的时候，我又重新触发这个网页的请求，session的图标则会这样呈现，这种情况下选中session，右键 > 属性 > X-ABORTED-WHEN查看请求被取消的时间，像我上面描述的情况一般X-ABORTED-WHEN都是SendingResponse。这种情况就是正常的，但是有一种情况就存在问题了。同样还是这个图标，但是session的返回值为5XX，这种应该就是服务器的问题，需要另外跟进


2. ![2015-19-3](/images/2015-12-19-3.png) 正在向服务器发送请求，![2015-12-19-4](/images/2015-12-19-4.png)和正在从服务器下载响应，这两种状态都是过程状态，不是该session的最终状态。


例如：当我从一个网站下载一个比较大的文件，如：某exe时，就很明显能够看到这个![2015-12-19-4](/images/2015-12-19-4.png)标志，当所有的response全部返回后（下载完成后），这个标志就会变成，意思就是：响应成功（下载成功），有兴趣可以去某官网上下载一个exe或者apk看一下效果
> 注：当然也不是所有的response完成后都是这个标志


3. ![2015-12-19-5](/images/2015-12-19-5.png) response是HTML或者XML。有时候会发现返回值是json，但实际上也是这个图标，原因是返回值的Content-Type: text/html


4. ![2015-12-19-6](/images/2015-12-19-6.png)请求使用了POST方法向服务发送数据。查看一个请求是get还是post在测试过程中还是很重要的（在不了解这个图标的含义之前，我是通过request有没有body来区分的，现在表示很囧~很low(⊙﹏⊙)b）


5. ![2015-12-19-7](/images/2015-12-19-7.png)重定向标志，返回码为302，快捷图标和返回码配合着看，意思会更明显


6. ![2015-12-19-8](/images/2015-12-19-8.png)服务器返回错误的标志，测试过程中需要特别注意（用红色呈现的，不注意到也不可能的哈）


7. ![2015-12-19-9](/images/2015-12-19-9.png)response是Flash。例如这条请求[](http://img1.126.net/channel12/021501/300250_1113.swf)
> 通过后缀就能看出文件类型哈


8. ![2015-12-19-10](/images/2015-12-19-10.png)response是图像文件。例如这条请求http://gb.cri.cn/mmsource/images/2014/08/29/nx20140829001.png（文件类型也是很明显）
9. ![2015-12-19-11](/images/2015-12-19-11.png)response是json格式
10. ![2015-12-19-12](/images/2015-12-19-12.png)response是脚本文件
11. ![2015-12-19-13](/images/2015-12-19-13.png)response是css
12. ![2015-12-19-14](/images/2015-12-19-14.png)response是xml文件
13. ![2015-12-19-15](/images/2015-12-19-15.png)response是视频文件。例如这条请求http://stv.cssn.cn/vod/cass/AD/2015/3/17/1426582795852.flv


















































