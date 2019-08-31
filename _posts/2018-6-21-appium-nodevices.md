---
layout: post
title: appium | log循环提示：0 device connect
categories: [Android]
description: some word here
keywords: keyword1, keyword2
---

### 问题描述
使用appium的过程中，一定要学会查看log，尤其是发生异常的时候。如下是连接不上设备的情况的日志
![2018-6-21-1](/images/2018-6-21-1.png)

这个时候，另开终端使用adb device查看会显示如下情况
![2018-6-21-2](/images/2018-6-21-2.png)

### 解决方案
使用appium前，确保adb连接正常，如果出现如上图所示信息，一般解决思路如下：
1. 重新插拔USB
2. 开发者选项关闭再打开
3. 切换手机连接PC的模式
4. 使用应用宝先连接成功，然后再启动appium
