---
layout: post
title: ABI相关问题总结
categories: [Android]
description: some word here
keywords: keyword1, keyword2
---

### 问题：
往android模拟器安装apk的提示INSTALL_FAILED_NO_MATCHING_ABIS:系统不支持的CPU架构

### 分析：
1. 确认apk支持的CPU架构

   使用jadx将apk解压,检查lib/ABI目录，一般情况下，目录列表是以下的其中一种或者几种：

    ① armeabiv-v7a（32位ARM设备）: 第7代及以上的 ARM 处理器。2011年15月以后的生产的大部分Android设备都使用它.  
    ② arm64-v8a（64位ARM设备）: 第8代、64位ARM处理器，很少设备，三星 Galaxy S6是其中之一。  
    ③ armeabi: 第5代、第6代的ARM处理器，早期的手机用的比较多。  
    ④ x86: 平板、模拟器用得比较多。  
    ⑤ x86_64: 64位的平板  

    **备注：**显示一种即只支持一种，显示两种的话就是支持两种（**注意：**显示的目录为2种的时，两个目录下的文件应该完全一样，才能支持两种CPU架构），如下图所示：
    ![](/images/2018-6-22-3.png)


2. 检查模拟器支持的CPU架构

  - 使用adb命令检查设置的cpu架构```adb shell getprop ro.product.cpu.abi```如图所示：![](/images/2018-6-22-4.png)
  - 虚拟机可以直接在编辑里面查看，如图所示：![](/images/2018-6-22-5.png)

### 解决方案
更换模拟器的CPU架构。更换模拟器的image，如下图所示：
  ![](/images/2018-6-22-1.png)

