---
layout: post
title: 手机连接Charles ，有需要访问外网的接口该怎么办
categories: [iOS]
description: some word here
keywords: keyword1, keyword2
---

### 一、问题描述

公司的业务都在国外，测试的过程中经常需要抓接口定位问题，而有的接口需要翻墙，用手机端翻墙的话，Charles上就完全看不到信息了

### 二、问题解决

1. 手机连接Charles
2. 电脑翻墙
3. 查看自己电脑端shadowsocket的HTTP 代理设置监听地址，如图所示，我的是127.0.0.1，端口1087

   ![](/images/2020-06-04-2.png)

4. 设置Charles，proxy > External Proxy Settings, 勾选Use external proxy servers,勾选web proxy 和 Secure Web Proxy, 填写上面的端口号。如图

   ![](/images/2020-06-04-1.png)

5. 在手机端访问一个需要翻墙的接口，或者直接在手机端浏览器里面使用谷歌浏览器，大功告成

### 三、最后

感谢小胖同学




