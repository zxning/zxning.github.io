---
layout: post
title: 《python 语言程序设计》练习题
categories: [python]
description: some word here
keywords: keyword1, keyword2
---

### 题目1：货币转换

人民币和美元间汇率固定为：1美元=6.78人民币。程序可以接受人民币或美元输入，转换为美元或人民币输出。人民币采用RMB标识，美元USD标识，符号和数值之间没有空格。

注意：
1. 获得输入请使用input() ；
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

### 题目2：温度转换1

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
### 题目3：温度转换2

转换算法同上，要求如下：

1. 输入输出的摄氏度可采用大小写字母C结尾，温度可以是整数或小数，如：12.34C指摄氏度12.34度
2. 输入输出的华氏度可采用大小写字母F结尾，温度可以是整数或小数，如：87.65F指摄氏度87.65度
3. 输出保留小数点后两位，输入格式错误时，输出提示：输入格式错误
4. 使用input()获得测试用例输入时，不要增加提示字符串

### 实现如下：

```
TempStr = input("")
if TempStr[-1] in ['F','f']:
    C = (eval(TempStr[0:-1]) - 32)/1.8
    print("{:.2f}C".format(C))
elif TempStr[-1] in ('C','c'):
    F = 1.8 * eval(TempStr[0:-1]) + 32
    print("{:.2f}F".format(F))
else:
    print("输入格式错误")
```
### 题目4：数字形式转换

获得一个用户输入的正整数，输出该数字对应的中文表示

### 实现如下：

```
template = "零一二三四五六七八九"               
a = input()                           
for i in a:                           
    print(template[eval(i)], end='')  
```
### 题目5：数值运算

获得用户输入的一个字符串，格式如下：M OP N   其中，M和N是任何数字，OP代表一种操作，表示为如下四种：+，—，*，/(加减乘除)根据OP，输出M OP N的运算结果，同意保存小数点后2位。
注意：M和OP、OP和N之间可以存在多个空格，不考虑输入错误情况


### 实现如下：
```

```

### 题目6：turtle正方形绘制

使用turtle库，绘制一个正方形

### 实现如下：

```
#PythonDraw.py
import turtle
turtle.setup(650,350,200,200)
turtle.penup()
turtle.fd(-250)
turtle.pendown()
turtle.pencolor("black")
turtle.pensize(5)
#turtle.seth()
turtle.forward(150)
turtle.left(90)
turtle.forward(150)
turtle.left(90)
turtle.forward(150)
turtle.left(90)
turtle.forward(150)
turtle.done()

```
### 题目7：turtle六边形绘制

使用turtle库，绘制一个六边形

### 实现如下：

```
#绘制六边形
import turtle
turtle.setup(650,650,200,200)
turtle.penup()
turtle.fd(-250)
turtle.pendown()
turtle.pencolor("black")
turtle.pensize(5)
#turtle.seth()
turtle.forward(150)
turtle.left(60)
turtle.forward(150)
turtle.left(60)
turtle.forward(150)
turtle.left(60)
turtle.forward(150)
turtle.left(60)
turtle.forward(150)
turtle.left(60)
turtle.forward(150)
turtle.done()
```


