---
layout: post
title: 多行数据按照中间某个值（时间）进行排序
categories: [Linux，VIM]
description: some word here
keywords: keyword1, keyword2
---

### 问题描述
拿到一份数据，里面的时间信息是乱的，如下图所示：
![](2015-12-20-sort1.png) 
但是只有按照时间顺序看才有意义，想到Linux处理数据比较强大，决定用Linux试一下,那么问题来了，我平时都是在windows上工作的，我怎样才能在Linux上处理数据呢。
### 解决方法
请教了小朋友，发现，其实我经常登录Linux服务器，只是自己没有意识到。而且，前两天刚刚申请了Linux虚机，现在派上用场了
1. 用winscp登录自己的虚拟,将要准备处理的文件拖到个人目录下
2. 使用putty登录虚机
3. 进入目标路径 cd /search/test
4. 尝试使用Linux的命令：ls -l 嗯~能看到我放的文件，再使用cat命令读取文件，嗯~可以读取。问题又来了，Linux下怎么对文件进行排序呢？经过百度，发现，Linux下有个强大的sort命令：
> sort -n 以数值进行排序，避免出现10比2大的情况
sort -k 2:对第二列进行升序的排序
sort -t [：以[作为分隔符
5. sort -n -k 2 -t [ test
> 文件名叫test

6. 结果如下：
![](2015-12-20-sort2.png)
