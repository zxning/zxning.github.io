---
layout: post
title: Appium | Locator Strategy 'css selector' is not supported for this session
categories: Python
description: 
keywords: 
---

appium问题集合

### 1. 问题描述

使用appium找元素用的 driver.find_element_by_id ，结果报错：selenium.common.exceptions.InvalidSelectorException: Message: Locator Strategy 'css selector' is not supported for this session

appium 3.17 去掉了 find_element_by_name ，想着怎么样也不能去掉by_id啊，查了查去，感觉最接近的就是版本不兼容

使用 ```python3 -m pip show selenium``` 查看本机安装的selenium版本是3.14.1

### 2. 解决方案

降级selenium

MAC，直接从安装目录下删除3.14.1版本的selenium，重新安装selenium 2.53.6 ```pip3 install selenium==2.53.6```



