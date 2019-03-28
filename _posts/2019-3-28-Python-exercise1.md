---
layout: post
title: python 语言程序设计练习题
categories: [python]
description: some word here
keywords: keyword1, keyword2
---

### 题目1：货币转换

人民币和美元间汇率固定为：1美元=6.78人民币。程序可以接受人民币或美元输入，转换为美元或人民币输出。人民币采用RMB标识，美元USD标识，符号和数值之间没有空格。

注意：
1. 这是一个OJ题目，获得输入请使用input() ；
2. 不提示输出格式错误，结果小数点后保留两位。


### 实现如下：

```
CoinStr = input("")
if CoinStr[0:3] in ['RMB','rmb']:
    C = eval(CoinStr[3:]) /6.78
    print("USD{:.2f}".format(C))
elif CoinStr[0:3] in ['USD', 'usd']:
    F = eval(CoinStr[3:]) *6.78
    print("RMB{:.2f}".format(F))
else:
    print("输入格式错误")
```

### 题目2：温度转换

编写程序将用户输入华氏度转换为摄氏度，或将输入的摄氏度转换为华氏度

转换算法如下：（C表示摄氏度，F表示华氏度）
C = (F - 32)/1.8
F = C * 1.8 +32

要求如下：
1. 输入输出的摄氏度采用大写字母C开头，温度可以是整数或小数，如：C12.34指摄氏度12.34度
2. 输入输出的华氏度采用大写字母F开头，温度可以是整数或小数，如：F87.65指华氏度87.65度
3. 不考虑异常输入的问题，输出保留小数点后两位
4. 使用input获得测试用例输入时，不要增加提示字符串

### 实现如下：

```
TempStr = input("")
if TempStr[0] in ['F','f']:
    C = (eval(TempStr[1:]) - 32)/1.8
    print("C{:.2f}".format(C))
elif TempStr[0] in ('C','c'):
    F = 1.8 * eval(TempStr[1:]) + 32
    print("F{:.2f}".format(F))
else:
    print("输入格式错误")
```
### 题目3：数字形式转换

获得一个用户输入的正整数，输出该数字对应的中文表示

### 实现如下：

```

```
### 题目4：：

### 实现如下：

```

```









