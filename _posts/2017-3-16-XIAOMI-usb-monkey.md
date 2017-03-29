---
layout: post
title: 小米手机运行adb install，monkey命令失败的解决方法
categories: [Android, adb]
description: some word here
keywords: keyword1, keyword2
---


### 问题一、

问题描述：在小米3手机上使用adb install命令的时候提示Failure [INSTALL_CANCELED_BY_USER]，实际上在手机上并没有弹出确认弹窗

解决方法：需要在小米3手机上，开发者选项中打开usb安装
![](/images/2017-3-16-1.png)

### 问题二、

问题描述：使用小米3手机运行monkey命令，每次跑两三秒就会失败

解决方案：​如下图所示，小米最新系统上默认关闭了该选项，打开就可以运行了
​
![](/images/2017-3-16-2.png)



 


