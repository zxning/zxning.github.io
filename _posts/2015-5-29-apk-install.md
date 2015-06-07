---
layout: post
title:一键给手机“安装驱动+apk”【适用于手机端测试童鞋】
categories: Android
description: some word here
keywords: keyword1, keyword2
---

 我猜测哈~很多手机端测试同学从PC上获取build之后，再使用adb命令将apk安装到手机中


 但是有没有那样的情况呢，输入命令之后，提示“找不到设备”，因为没有安装驱动……纳尼？！……关键时刻怎能如此掉链子, 神器登场--等等等---安装器

**环境配置一：**
**前提：**安装了搜狗输入法
**步骤：**

1. 桌面-->右键-->新建 快捷方式

2. 在%public%\SogouInput\USBDT    路径下找到MobAssHelper.exe

3. 复制MobAssHelper.exe的路径并传参数 -addasso  ，如下所示
    ![2015-5-29-1](/images/2015-5-29-1.png)

4. 输入路径后，点击“下一步”，再给快捷方式命名，例如：安装器，点击“完成”

5. 右键“以管理员方式启动”新创建的“安装器”快捷方式------所有的apk自动关联到了安装器，需要安装该apk时，连接手机，双击该apk即可。。。

6. 大功告成，以后再也不用担心安装启动神马东西啦……O(∩_∩)O哈哈~……so easy
      

**环境配置二：**
**前提：**安装了搜狗 浏览器
**步骤：**

1. 右键-->新建 快捷方式

2. 在%appdata%\Roaming\SogouExplorer\Bin\Android 路径下找到MobAssHelper.exe

3. 复制 MobAssHelper.exe的路径并传参数 -addasso  ，如下所示
         ![2015-5-29-2](/images/2015-5-29-2.png)        

4. 其他步骤同上

个人建议配置环境一，因为该处更新比较及时…



  
