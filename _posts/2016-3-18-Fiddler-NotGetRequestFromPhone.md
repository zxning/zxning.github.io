---
layout: post
title: Fiddler突然不能抓手机端请求的原因之一
categories: [Android, Fiddler]
description: some word here
keywords: keyword1, keyword2
---

### 问题描述
Fiddler突然不能抓手机端的请求了（可以抓PC端的请求），核对了以下信息，确认都正确

1.	PC端和手机端均能上网
2.	ping手机端IP ，能ping通
3.	手机端设置代理的IP和端口号正确
4.	Fiddler options里面的设置也正确
5.	重启手机，电脑
6.	重装Fiddler

### 解决方案
#### 原因
后来找到问题：被防火墙拦住了，如下图所示
![](/images/2016-3-18-1.png)
 
####解决方案1
双击被拦截的防火墙，将“操作”处勾选“允许连接”并确定
![](/images/2016-3-18-2.png)
 
####解决方案2
或者在“Windows防火墙”>”允许程序或是功能通过Windows防火墙”>“勾选Fiddler”并确定
![](/images/2016-3-18-3.png)
 
###后记
猜测出现这个问题的原因可能是，当某次打开fiddler的时候弹出如下窗口，点击了“取消”按钮
![](/images/2016-3-18-4.png)



 


