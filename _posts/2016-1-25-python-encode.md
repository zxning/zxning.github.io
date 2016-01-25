---
layout: post
title: Python|提示错误：Non-ASCII character in file
categories: [Python]
description: some word here
keywords: keyword1, keyword2
---

### 问题描述
运行Python代码后，出现错误：

```python 
SyntaxError: Non-ASCII character '\xe5' in file，but no encoding declared
```

奇怪的是，我在代码的开头已经增加` # -*- coding: UTF-8 -*-   `，如下所示：
![](/images/2016-1-25-coding.png)

### 问题分析

原来是需要将`  # -*- coding: UTF-8 -*-`
写在代码的最开始的位置，即使最上面是注释也要放在注释的上面，调整成如下格式后，顺利通过
![](/images/2016-1-25-coding2.png)


详情可以查看[python 官方文档](https://www.python.org/dev/peps/pep-0263/)


