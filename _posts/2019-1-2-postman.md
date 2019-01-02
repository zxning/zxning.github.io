---
layout: post
title: Mac | 使用postman+newman+Jenkins配置线上接口自动监控（三）
categories: [Interface]
description: some word here
keywords: keyword1, keyword2
---

### 问题总结

1. 问题一：调用cmd命令失败，具体错误如下所示：
    ![](/images/2019-1-2-1.png)

解决方法：由于是在Mac上配置的，但选择的是Windows的批处理命令，如下所示，修改为shell命令


2. 问题二：找不到newman命令
    ![](/images/2019-1-2-2.png)

解决方法：在Jenkins的配置处增加环境变量export PATH


3. 问题三：打不开文件夹，如下所示：
    ![](/images/2019-1-2-3.png)

解决方法：如何打开没有权限的文件，右键>显示简介，打开右下角的锁，修改权限，然后就可以打开了

