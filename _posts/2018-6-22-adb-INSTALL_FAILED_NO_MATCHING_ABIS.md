---
layout: post
title: adb | INSTALL_FAILED_NO_MATCHING_ABIS
categories: [adb,Android]
description: some word here
keywords: keyword1, keyword2
---

### 一、问题描述
往android模拟器安装apk的提示INSTALL_FAILED_NO_MATCHING_ABIS

### 二、解决方案
根据网上了解到的情况，应该是要更换模拟器的CPU架构。更换模拟器的image，如下图所示：
  ![](/images/2018-6-22-1.png)

### 三、如何确认APP支持的CPU架构
1. 将apk解压
2. Android应用支持的ABI取决于APK中位于lib/ABI目录中的.so文件，其中ABI可能是上面说过的七种ABI中的一种   检查lib目录，查一下so文件所在目录，如下所示：
  ![](/images/2018-6-22-2.png)
3. 因此，可以确定该apk支持的CPU 架构是armeabi-v7a

### 四、Android 设备的CPU类型(通常称为”ABIs”)

Android系统目前支持以下七种不同的CPU架构：
ARMv5，最早，Android 系统只支持 ARMv5 的 CPU 构架
ARMv7 (从2010年起)，第7代及以上的 ARM 处理器。2011年15月以后的生产的大部分Android设备都使用它.
ARMv8，第8代、64位ARM处理器，很少设备，三星 Galaxy S6是其中之一
MIPS (从2012年起)，
MIPS64，
x86 (从2011年起)，平板、模拟器用得比较多
x86_64 (从2014年起)，64位的平板
每一种 CPU 构架，都定义了一种 ABI（Application Binary Interface），ABI 决定了二进制文件如何与系统进行交互


http://blog.csdn.net/xx326664162/article/details/51163905
