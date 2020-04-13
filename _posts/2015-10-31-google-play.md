---
layout: post
title: 非原生手机安装 Google Play闪退的问题
categories: [Android]
description: some word here
keywords: keyword1, keyword2
---

### 问题描述

由于需要从Google商店中下载APP进行验证，从PC网页的Google商店登陆后，找到对应APP点击下载后，一直提示没有在设备上验证账户【问题1】  

根据提示，在手机端下载Google商店后打开一直发生闪退【问题2】，网上相关的方法众多，但是各种尝试一直显示“Google服务已停止”，各种尝试后终于安装成功了，在此备忘下（目前暂不确定原因，有可能是GoogleServicesFramework安装包有问题）

### 解决方法

1. 手机root并安装了root exlpore工具  
2. 下载[GoogleServicesFramework.apk](http://pan.baidu.com/s/1dEk4sxz)和[google Play.apk](http://pan.baidu.com/s/1nuimjUx)
3. 安装上面两个软件，不要打开
4. 使用root explorer工具把已经安装的上面两个APP从用户目录（data/app）复制到系统目录（system/APP）
5. 关机，开机
6. OK，Google商店可以打开了，【问题2】解决
7. 在设置 > 账户中添加Google账户并登陆(可在手机端的Google商店直接安装)，连接PC，在网页的Google商店上就能够下载对应的APP了【问题1】解决

### 遗留问题
  
使用两款手机（索尼L36h， 三星note3）均不会再闪退，但是从设置中添加Google账户会导致设置无响应——作为后续TODO
