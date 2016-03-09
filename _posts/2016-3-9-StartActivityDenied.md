---
layout: post
title: 使用appium调起activity失败的问题
categories: [Android, appium]
description: some word here
keywords: keyword1, keyword2
---

### 问题描述
代码如下：欲实现启动一app的某一个activity
```
        desired_caps = {}
        desired_caps['platformName'] = 'Android'
        desired_caps['platformVersion'] = '5.1.1'
        desired_caps['deviceName'] = '01ac1a551e5a695f'
        desired_caps['appPackage'] = '包名'      
        desired_caps['appActivity'] = 'activity名'
        self.driver = webdriver.Remote('http://localhost:4723/wd/hub', desired_caps)
```
结果报错，log如下：
![](/images/2016-3-9-1.png)

### 问题分析
1. 使用log分析原因

将log中使用的命令在cmd中运行后，同样出现错误，如下
![](/images/2016-3-9-2.png)
根据错误提示：该activity没有导出，猜测程序的AndroidManifest对该activity声明时，export=false。但是我之前曾经在一个手机上成功启动过该activity。请教大神后，大神腿短可能是因为那个手机上的 adb 有 root权限。问题分为两方面：

a. 使用su运行上面的命令。
b. 现在使用的手机，adb是否有root权限,如果没有，是否可以提权 

*注1：看 adb 是否有 root 权限你就运行 adb shell，如果是 $，就是普通权限，如果是 #，就是 root 权限*

*注2：为了确认该activity的属性，后来使用apktool将apk包反编译后搜索到对应的activity，果然存在属性exported="false"*


2. 根据推测进行验证

a. 使用su 启动上面的命令，运行正确，调起了acticity页面
b. 使用adb root之后提示''' adbd cannot run as root in production build''',一方面大神说有app可以解决这个问题，另一方面搜索adb root之后，发现大家都在推荐一个超级adb的app
c. 安装 adbd insecure 之后，勾选如下图所示
![](/images/2016-3-9-3.png)

*注：下载adbd  insecure 之后，由于下载的版本比较低，而我使用的是Android5.1系统的手机，因此出现devices not found 和offline 两种问题，分别在不同的手机上，后来下载最新版本后，这个问题就解决了*
d. 重启启动adb，问题得到解决

### 总结
1. 使用appium的过程中要学会查看log
2. adb的工作原理了解的不是很清楚，后来需要再进行深入了解

