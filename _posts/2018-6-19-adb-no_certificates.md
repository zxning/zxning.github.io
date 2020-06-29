---
layout: post
title: adb | INSTALL_PARSE_FAILED _NO_CERTIFICATES
categories: [Android]
description: some word here
keywords: keyword1, keyword2
---

### 问题描述

下载apk包，使用adb install命令安装时提示：没有签名，见如下截图
![](/images/2018-6-19-1.png)

### 解决方案

1. 第一想法是没有签名，但实际上是有的
2. 由于下载的过程中网速比较慢，因此怀疑下载出错，导致apk错误。为了验证该想法，当网速比较好的时候下载包可以正常安装的时候，比对了MD5值，果然，错误包和正常包的MD5值不一样，但size是一样的

### 总结

使用adb install安装apk时，如提示没有签名，除了真的没有签名以外，还有一种原因就是下载过程出错导致没有检查到签名文件
