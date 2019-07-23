---
layout: post
title: 随机32位ID，拼接URL请求获取返回值后，根据首字母
categories: [python，interface]
description: some word here
keywords: keyword1, keyword2
---

### 需求

服务端根据用户ID的首字母将用户三等分（mod 3），每一份下发不同的json，

### 需求分析

任务分析：

1. 随机的策略由于是伪随机，大概差不多就行，不用测试
2. 首字母是0,3,6,9,c,e下载json1
3. 首字母是1,4,7,a,d,f下载json2
4. 首字母是2,5,8,b,d下载json3

根据以上任务内容，需求拆分如下：

1. 随机32位用户ID，存到data中
2. 将上面的data按照mod分组，符合分组的，去请求URL，
3. 将不同ID的请求结果，取关键字和预期关键字进行比较

### 分模块功能实现如下：

1. 写死一个ID，使用urllib库进行请求

![](/images/2019-7-17-1.png)
2. 写死一个ID，使用request库进行请求

![](/images/2019-7-17-2.png)

3. 将随机部分的封装一个函数

![](/images/2019-7-17-3.png)

### 完整代码如下：

