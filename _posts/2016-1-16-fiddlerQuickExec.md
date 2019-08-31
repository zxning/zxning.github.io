---
layout: post
title: Fiddler | QuickExec
categories: [Fiddler]
description: some word here
keywords: keyword1, keyword2
---

最近在做项目时，发现Fiddler一个很实用的功能：QuickExec，如下图所示（Fiddler 左下角）：
![](/images/2016-1-16-fiddler1.png)

### 定位 request/response 在特定的tab上

由于我所在的项目和服务端交互都是使用的 json，没有被格式化的 json 看着闹心，因此，每次都是通过 Inspectors > Response > JSON tab查看，操作路径是：

1. 鼠标点击选中一个session
2. 在Resquest 区域点击Inspectors
3. 在Response 区域点击JSON tab

如果只操作一两次就还行，如果每天要操作成百上千次就会在这个小步骤上浪费一些时间。还有一种方法就是双击session，能够达到Inspectors tab下面，但是 Fiddler 总是根据该session的类型，从而自动决定该session的Response tab，例如，双击一个image类型的session，则response tab 一定优先在ImageView tab 上，有没有优化的空间，可以自定义显示吗？
    
- 解决方案： 在QuickExec输入命令``` PREFS SET fiddler.ui.inspectors.response.alwaysuse “json” ```, 双击session，则可以看到Response tab被自动定位到JSON上了
- 同理，```PREFS SET fiddler.ui.inspectors.request.alwaysuse "webforms"```可以使session的resquest默认显示在webforms的tab上

### 快速找到所有的post请求

所有post请求的图标都是带有向右的小箭头的那种，如果能让所有向右的小箭头都高亮显示就好了

解决方案：输入命令：=post 然后点击enter键回车，可以看到所有的post请求都是以蓝色的底色显示，如下图所示：
![](/images/2016-1-16-fiddler2.png)

另外：这个方法也适用于迅速找出=Result code 的情况，例如：=404

### 搜索文本

使用Ctrl+F 可以对session中的字符进行搜索，除了使用该功能外，使用QuickExec也可以完成搜索功能，格式为：？关键字。例如：？qq  搜索结果如下：
![](/images/2016-1-16-fiddler3.png)

### 将含有某关键字的session加粗显示

格式为：bold 关键字，例如：bold baidu
![](/images/2016-1-16-fiddler1.png)

回车后，重新请求，可以看到含有关键字“baidu”的请求都被加粗显示，状态栏显示正在执行的命令是：``` Bolding request for baidu```. 如果后续想要加粗其他字段该怎么办呢？

Tool > Reset Script可以解决这个问题。重置之后，加粗的状态则会消失

### 写在最后：

使用上下箭头可以查看上一个和下一个使用过的命令~方便编写哦~O(∩_∩)O~


