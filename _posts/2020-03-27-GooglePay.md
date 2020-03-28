---
layout: post
title: GooglePay测试点以及问题总结
categories: [Android]
description: some word here
keywords: keyword1, keyword2
---

APP接入Google play之后，如何开展测试以及可能遇到的问题，做个备忘

### 一、测试准备

1. 管理员先向Google play的测试通道上传apk包
2. 每个人最好有2个gmail账号（虽然不同的手机可以共用一个账号，但是，如果A手机订阅了，B手机的订阅状态可能会受影响，因此建议，一个手机一个账号）
3. 需要管理员配置沙河测试人员：即将上一步申请的gmail账号的账号添加上
4. 在测试手机上用刚才申请的账号登录Google账户，并且访问邀请链接，点击按钮become tester（邀请链接一般都是：替换其中的包名即可： https://play.google.com/apps/testing/com.xxx.xxxxx）

    ![](/images/2020-03-27-1-1.png)


### 二、测试点

持续更新中……

    ![](/images/2020-03-27-1.png)

### 三、问题总结

1. 系统无法找到你要购买的商品

   ![](/images/2020-03-27-2.png)

    原因：APP被下架

2. 点击购买后，需要添加付款方式

    ![](/images/2020-03-27-3.png)

   原因：账号没有被加入到测试组中，可以到这个链接下查看 https://play.google.com/apps/testing/com.xxx.xxxxx （后面是包名）, 会显示这个
    
    ![](/images/2020-03-27-4.png)

3. 系统正在处理您的订单

    原因：该账号已经购买过该订单，正在处理中（如果已经换了设备，点击restore，即可把订阅状态同步过来）

4. 刚刚购买，杀APP重启，还是未购买状态 *重要，而且是偶现的，需要注意*

    原因：拉历史订单的时候，默认是按照倒序返回的，但是Google有bug，有时候会把最近一次的购买顺序排错，因此，需要开发手动校对时间戳

5. 做国际化产品，如果在不同的地区要显示不同的价格的话，需要用对应区域的账号，如何确定自己的账号是哪个区的？

    在Google payment中查看

### 注意事项

1. 账号加入测试组后，不用点击按钮“become tester” 也是可以的

2. 账号加入测试组后，有时候需要等一会儿才能生效，一般是15分钟

3. google订阅通常会有3天免费或者7天免费，这个是在后台设置的，测试环境测试的时候，如果已经购买过了是看不到免费状态的。只有用新账号会看到3分钟的免费提示

4. 购买月，五分钟到期，会自动续费6次，一共是半个小时后，自动取消订阅

5. 反复操作订阅和取消订阅后，谷歌商店的已订阅页面会出现查询不到订单的情况，这种情况很难处理，最简单的办法就是换个账号，让出现错误的账号过几天再用

6. 取消订阅后如果有对应的业务逻辑一定要注意“一律拒绝”逻辑

   ![](/images/2020-03-27-5.png)

[参考链接：https://developer.android.google.cn/google/play/billing/billing_testing](https://developer.android.google.cn/google/play/billing/billing_testing)

