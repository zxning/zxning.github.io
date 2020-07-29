---
layout: post
title: Pytest | No module named 'xxx'
categories: Python
description: 
keywords: 
---

### 1. 问题描述

在pycharm中运行py文件是可以的，但是在terminal中运行就报出 No module named 'xxx' ，如下图所示：

![](/images/2020-07-29-1.png)

目录结构如下所示：

![](/images/2020-07-29-2.png)


### 2. 解决方案

在运行的py文件中，本处指的是：test_in_login.py，增加如下内容

```
import os
import sys
sys.path.append("/Users/zhaoxining/Documents/api_pytest")
```

再次运行，结果如下：

![](/images/2020-07-29-2.png)