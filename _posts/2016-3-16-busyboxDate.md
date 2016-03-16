---
layout: post
title: 使用busybox命令快速查看时间戳
categories: [linux]
description: some word here
keywords: keyword1, keyword2
---

### 一、问题描述
测试过程中需要读懂配置文件中的时间戳才能进一步完成测试，例如：
![](/images/2016-3-16-1.png)
问题是：如何快速将时间戳转换成人可识别的时间呢


### 二、解决方案1
利用在线时间戳转换工具进行转换，例如：

[工具1](http://tool.chinaz.com/Tools/unixtime.aspx)

[工具2](http://www.epochconverter.com/)

*注：工具2的优点是不用去掉时间戳的后三位，可以全部复制之后进行转换。工具1之前需要摘掉后三位进行转换，现在也可以直接复制全部内容进行转换了*

### 三、解决方案2
使用busybox 的date命令。使用方法：busybox date -d @1457894523

当然，要使用busybox命令，首先需要手机中存在busybox，在adb shell下直接输入busybox，查看是否存在，如不存在则返回“busybox: not found”，解决方法：

**1. 拷贝本地busybox到手机，adb push "d:\busybox" /data/local/tmp/**

**2. 拷贝busybox到system/xbin下面**

**3. 修改busybox的权限**


###四、遇到的问题及解决方案


1. 移动到xbin的时候，会提示目录只有只读权限，如下图所示
    ![](/images/2016-3-16-2.png)

    **解决方法：**

    1. adb shell su
    2. mount -o remount rw /system
    3. 然后copy成功


2. 将busybox拷贝到xbin目录下成功后，输入busybox，弹出如下错误
    ![](/images/2016-3-16-3.png)

    **解决方法：**

    1. 进入xbin目录下
    2. 给busybox 777权限```chmod 777 busybox```
    3. 然后再输入busybox，则能看到busybox的版本，以及使用方法的相关信息，然后就可以使用busybox的date命令进行时间戳转换了。如下图所示：


    ![](/images/2016-3-16-4.png)

    ![](/images/2016-3-16-5.png)


3. 已经将busybox拷贝到手机中，但是使用时出现busybox:not found
    ![](/images/2016-3-16-6.png)

    **解决方法:** 没有将busybox拷贝到system/xbin的目录下。

*注：*/system/xbin目录相当于在windons已经被加入到path路径下


