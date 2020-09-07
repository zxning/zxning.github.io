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

### 问题分析: 使用log
将log中使用的命令在cmd中运行后，同样出现错误，如下
![](/images/2016-3-9-2.png)
根据错误提示：该activity没有导出，猜测程序的AndroidManifest对该activity声明时，export=false。But,我之前曾经在一个手机上成功启动过该activity。请教大神后，推断可能是因为那个手机上的 adb 有 root权限。接下来，从两个方面来看这个问题：

1. 使用su运行上面的命令。
2. 现在使用的手机，adb是否有root权限,如果没有，是否可以提权 

*注1：看 adb 是否有 root 权限你就运行 adb shell，如果是 $，就是普通权限，如果是 #，就是 root 权限*

*注2：为了确认该activity的属性，后来使用apktool将apk包反编译后搜索到对应的activity，果然存在属性exported="false"*


### 分析验证
1. 使用su 启动上面的命令，运行正确，调起了acticity页面，说明adb提权后确实可以调起属性export=false的activity
2. 当前使用的手机，使用adb root提权之后提示''' adbd cannot run as root in production build''', 根据报错，搜索adb root之后，发现大家都在推荐一个APP，叫： adbd insecure 
3. 安装 adbd insecure 之后，勾选如下图所示
![](/images/2016-3-9-3.png)
4. 重启adb，运行appium，成功调起activity.Oh~~Yeah

*注：下载adbd  insecure 之后，由于下载的版本比较低，而我使用的是Android5.1系统的手机，因此出现devices not found 和offline 两种问题，分别在不同的手机上，后来下载最新版本后，这个问题就解决了*


### 备注
1. 使用appium的过程中要学会查看log
2. adb 的运行原理是 PC 端的 adb server 与手机端的守护进程 adbd 建立连接，然后 PC 端的 adb client 通过 adb server 转发命令，adbd 接收命令后解析运行。
所以如果 adbd 以普通权限执行，有些需要 root 权限才能执行的命令无法直接用 adb xxx 执行。这时可以 adb shell 然后 su 后执行命令，也可以让 adbd 以 root 权限执行，这个就能随意执行高权限命令了



