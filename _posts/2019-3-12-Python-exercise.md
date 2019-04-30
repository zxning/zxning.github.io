---
layout: post
title: python 学习练习题
categories: [python]
description: some word here
keywords: keyword1, keyword2
---

### 题目1：根据给定的体重和身高计算肥胖程度

### 实现如下：

```
weight = 70
height = 1.61

bmi = weight/(height*height)
if bmi < 18.5:
    print("过轻")
elif 18.5 < bmi < 25:
    print("正常")
elif 25 < bmi < 28:
    print("过重")
elif 28 < bmi < 32:
    print("肥胖")
else:
    print("严重肥胖")

#题目：计算1~100的和
sum = 0
for x in range(101):
    sum = sum + x
print(sum)
```

### 题目2：逐个打印出L中的名字

### 实现如下：

```
L = ['Bart', 'Lisa', 'Adam']
for name in L:
    print(name)
```
```
L = ['Bart', 'Lisa', 'Adam']
for x in L:
    print('Hello,',x,'!')
```
### 题目3：打印出10以内的奇数

### 实现如下：

```
n = 0
while n < 10:
    n = n + 1
    if n % 2 == 0: # 如果n是偶数，执行continue语句
        continue # continue语句会直接继续下一轮循环，后续的print()语句不会执行
    print(n)
```
### 题目4：请定义一个函数quadratic(a, b, c)，接收3个参数，返回一元二次方程：ax^2 + bx + c = 0的两个解。提示：计算平方根可以调用math.sqrt()函数：

### 实现如下：

```
import math

a = input('请输入a的值：')
b = input('请输入b的值：')
c = input('请输入c的值：')
a = int(a)
b = int(b)
c = int(c)
def quadratic(a, b, c):
    if not isinstance(a+b+c, (int,float)):
        raise TypeError('bad operand type')

derta = b * b - 4 * a * c
if a!=0:
    if derta < 0:
        print('该方程没有实根')
    else:
        x1 = (-b + math.sqrt(b*b - 4*a*c))/2*a
        x2 = (-b - math.sqrt(b*b - 4*a*c))/2*a
        print(x1)
        print(x2)
else:
    x = -(c / b)
    print(x)
```

### 题目4：打印文本进度条

### 实现如下：

```
#\r回退，退格删除
#刷新的本质就是删除旧的
import time
scale = 50
print("执行开始".center(scale//2, "-"))
start = time.perf_counter()
for i in range(scale + 1):
    a = '*' * i
    b = '.' * (scale - i)
    c = (i/scale) * 100
    dur = time.perf_counter() - start
    print("\r{:^3.0f}%[{} -> {}]{:.2f}s".format(c, a, b, dur), end="")
    time.sleep(0.1)
print("\n"+"执行结束".center(scale//2, '-'))
```









