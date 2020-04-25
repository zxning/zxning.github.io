---
layout: post
title: python | 自动化实现从Jenkins上下载最新包并自动安装
categories: [python]
description: some word here
keywords: keyword1, keyword2
topmost: true
---

## 需求：
自动从Jenkins上下载最新包并安装到手机上

### 需求拆解：
1. 打开一个网址（发一个URL请求）
2. 寻找对应分支
3. 寻找对应分支的最新版本
4. 下载包
5. 存放包
6. 用adb命令安装

### 代码实现
![](/images/2019-1-10-1.png)


### 问题说明
1. 取包方法：最初想到取包的方法是根据打包页面的源码找下载地址，没有头绪，后来经人提醒，Jenkins的包都是放在固定地方的，只要找到固定的下载路径，固定名字就可以了。然后发现一件很棒的事情，我们的包名和分支名一样。哈哈。在下载页面对将要下载的包，右键 > 复制下载链接地址，即可找到apk包的下载地址 
2. 由于Jenkins需要登录，因此访问的时候需要考虑登录
3. with open打开的是一个文件，需要指定文件名，而不能是指定get(URL)的对象

### 需要优化的地方：

1. 一个项目通常有多个分支，如更换分支，则要修改代码中的路径
2. 如果每次打包的名字有变化的话，不适用

## 更新需求
1. 每次安装之前先检查本地是否存在安装包，如果存在则删除，如果不存在，则直接安装
2. 每次删除安装包的时候同时删除本地的隐藏文件.XXXX

### 代码实现
![](/images/2019-1-10-2.png)


### 优化后
本次主要优化的封装逻辑
···
#!/usr/bin/python
# coding=utf-8

import requests
import os
from requests.auth import HTTPBasicAuth
import time

def installApk():
    url = "http://192.168.1.11:8080/job/AndroidYellow/lastSuccessfulBuild/artifact/Yellow/app/build/outputs/apk/googleplay/debug/Lemon2.1.1_googleplay_debug.apk"

    # 登录Jenkins并请求URL
    response = requests.get(url, auth=HTTPBasicAuth("build","build"))
    # 提取URL的文件名
    filename = os.path.basename(url)
    # 打开上述文件并写到本地
    with open(filename, 'wb') as apk:
        apk.write(response.content)

    # 对本地文件执行adb命令
    os.system("adb install " + filename)


def DeleteData():
    os.system("adb shell rm -fr /sdcard/.boo*")


def UnstallApk():
    package_name = "com.social.lemon"
    # os.popen的返回结果是在一个文件中，需要读取，而且读取结果是列表
    result = str(os.system("adb shell pm list packages | grep lemon"))
    if result.find(package_name):
        os.system("adb uninstall " + package_name)
        time.sleep(10)
    else:
        pass

if __name__ == '__main__':
    DeleteData()
    UnstallApk()
    installApk()

···






### 需要优化的地方
1. 代码中应该尽量少用sleep，在使用adb uninstall 的时候，应该是拿到回调之后再去执行adb install 
