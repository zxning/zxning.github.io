---
layout: post
title: Python | unicode equal comparison failed
categories: [Python]
description: some word here
keywords: keyword1, keyword2
---

### 问题描述
代码运行后提示如下错误：

``` UnicodeWarning: Unicode unequal comparison failed to convert both arguments to Unicode - interpreting them as being unequal```

代码的细节：

```

# -*- coding: UTF-8 -*-  
'''
Created on 2016.1.25日

@author: test
'''

# import unittest
import time
from appium import webdriver

desired_caps = {}
desired_caps['platformName'] = 'Android'
desired_caps['platformVersion'] = '6.0'
desired_caps['deviceName'] = '03b25e23437f1056'
desired_caps['appPackage'] = '待测试的apk的包名'
desired_caps['appActivity'] = '待测试的apk的需要启动的activity'

driver = webdriver.Remote('http://localhost:4723/wd/hub', desired_caps)
time.sleep(2)

driver.find_element_by_name('文字').click()
time.sleep(5)
driver.find_element_by_name('文字1').click()
element1 = driver.find_element_by_name('文字2').text
if element1:
    if element1 != '文字2':
        print 'fail'
    else:
        print 'pass'
```

### 问题分析

1. 根据错误提示，找到出现问题的地方是比对文字：

 ``` if element1 != '文字2':```

- **加print输出**，如下所示：

```
str = '文字2'
print [element1]
print [str]
```
- **结果：**
![](/images/2016-1-25-Unicode2.png)

2. google 错误提示，得到如下答案：

    > your error message indicates that you aren't comparing unicode objects. You are probably comparing a unicode object to a str object
    *[链接地址](http://stackoverflow.com/questions/18193305/python-unicode-equal-comparison-failed)*


### 解决方案
两种

1. 都转换成Unicode进行比较

```
if element1:
    if element1 != u'文字2':
        print 'fail'
    else:
        print 'pass'
```

2.  在代码开头引入 ```from __future__ import unicode_literals  ```



