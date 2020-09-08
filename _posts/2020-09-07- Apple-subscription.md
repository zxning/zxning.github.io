---
layout: post
title: 苹果APP订阅点总结
categories: APP
description: 
keywords: 
---

### Apple 手机订阅测试点

#### 需求：

订阅套餐A：monthly银卡会员,送1200金币，2个喜欢
订阅套餐B: monthly金卡会员，送6500金币，5个喜欢
订阅套餐C：monthly铂金卡会员，送14000金币，15个喜欢

#### 测试点：

1. 单独订阅其中一个套餐，价格，赠送的金币等都正确
2. 单独订阅其中一个套餐后，续订后，给的内容都正确
3. 订阅后升级/降级套餐，扣钱就赠送对应的金币或者喜欢（没扣钱就不会赠送），续订后按照升级/降级后的套餐赠送
4. 同一个设备，同一个苹果账号，订阅后，删除账号再注册，点击restore，会将会员状态同步过来（金币状态不能同步）
5. 同一个设备，同一个苹果账号，订阅后，删除账号再注册，相同的套餐不能再订阅，换套餐要能订阅成功
6. AB两个设备，同一个苹果账号，A设备订阅后，B设备再次订阅都会失败，restore也会失败（只能restore已注销用户的会员状态）

#### 备注：苹果APP沙河账号的测试时间

![](/images/2020-09-07-1.png)


[参考链接：https://help.apple.com/app-store-connect/#/dev7e89e149d](https://help.apple.com/app-store-connect/#/dev7e89e149d)