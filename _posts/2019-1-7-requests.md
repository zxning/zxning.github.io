---
layout: post
title: Python | ImportError：No module named requests
categories: [python]
description: some word here
keywords: keyword1, keyword2
---

导入requests时，遇到了两个问题，错误都是No module named requests

### 问题一

在终端使用pip install requests安装requests后，在pycharm中import requests,然后在pycharm中运行代码后，仍然显示No module named requests

###解决方法

在pycharm中使用terminal安装requests之后，问题解决，也没有深究

![](/images/2019-1-7-0.png)

### 问题二

如上的代码在pycharm运行良好之后，在系统终端运行的时候，又出现了上面的错误

![](/images/2019-1-7-1.png)

### 查找原因

由于Mac上可以同时安装多个Python版本，系统默认版本Python2.7。Pycharm我选择的版本是3.7。

Pycharm中的requests模块是在Pycharm的terminal中安装的，安装到了Python3.7的目录下，Python2.7目录没有requests模块，因此报错

### 解决方法

1. 修改系统默认的Python版本，改成和pycharm一样的版本，结果发现，这俩版本都在环境变量的路径下，方法1失败
2. 在终端运行的时候指定版本，如下所示：

![](/images/2019-1-7-2.png)

### 备注

在pycharm中安装requests模块也可以如下操作：

1. Pycharm > Preference > Project Interpreter 
2. 点击+在跳出来的界面搜索requests模块进行安装

![](/images/2019-1-7-2.png)


