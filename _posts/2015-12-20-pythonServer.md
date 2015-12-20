---
layout: post
title: 使用python搭建临时server并访问一个接口
categories: [工作效率]
description: some word here
keywords: keyword1, keyword2
---

### 问题描述
最近需要对外演示fiddler的TextWizard功能，因此，需要访问一个接口，而且希望里面接口的返回值里面有encode过的内容。为了避嫌，不想使用项目上正在使用的接口，因此，打算自己写一个，需要做两件事情
1. 有个服务器供我放这个接口
2. 有个json文件
### 服务器的解决办法
1. 使用现成的测试服务器
2. 有Linux虚机，自己搭一个服务器
3. 曾经有个大神跟我说可以使用python自己临时搭一个
### json文件
1. 仿照服务器上的json文件写了一个，如下：

