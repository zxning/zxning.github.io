---
layout: post
title: adb报错|INSTALL_FAILED_NO_MATCHING_ABIS
categories: [adb]
description: some word here
keywords: keyword1, keyword2
---

### 问题描述
往android模拟器安装apk的提示INSTALL_FAILED_NO_MATCHING_ABIS

### 解决方案
根据网上了解到的情况，应该是要更换模拟器的CPU架构。更换模拟器的image，如下图所示
![](/images/2018-6-22-1.png)

### 如何确认APP的架构
1. 将apk解压
2. 查一下so文件所在目录，如下所示
![](/images/2018-6-22-2.png)
3. 因此，可以确定该apk支持的CPU 架构是armeabi-v7a

### Android 设备的CPU类型(通常称为”ABIs”)
armeabiv-v7a: 第7代及以上的 ARM 处理器。2011年15月以后的生产的大部分Android设备都使用它.
arm64-v8a: 第8代、64位ARM处理器，很少设备，三星 Galaxy S6是其中之一。
armeabi: 第5代、第6代的ARM处理器，早期的手机用的比较多。
x86: 平板、模拟器用得比较多。
x86_64: 64位的平板
