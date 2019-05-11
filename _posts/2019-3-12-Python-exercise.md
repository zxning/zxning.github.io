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
    if not isinstance(a+b+c, (int,float)):       #isinstance判断一个对象是不是已知类型。这里额意思是判断a+b+c是不是整型或者浮点型，如果不是已知的这两种类型，则执行下一句
        raise TypeError('bad operand type')      #使用raise来抛出一个异常（异常类型必须是Python提供的），并输出：操作数类型错误


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

### 题目4：打印文本进度条，输出如下图所示:

![](/images/2019-5-11-1.png)

### 实现如下：

```

#\r回退，退格删除
#刷新的本质就是删除旧的,sleep一会，再输入新内容
import time
scale = 50                              #总长度是50
print("执行开始".center(scale//2, "-"))  #"执行开始"居中，其他的填充-，总长度为25
start = time.perf_counter()             #测量时间函数，记录当前的时间，一般是连续调用取差值
for i in range(scale + 1):
    a = '*' * i                         #先填充的第一部分字符*
    b = '.' * (scale - i)               #后填充的第二部分.  *和.加起来共50个
    c = (i/scale) * 100                 # 显示的百分比
    dur = time.perf_counter() - start   # 从当前时间减去之前记录的时间就是这个过程花费的时间
    print("\r{:^3.0f}%[{} -> {}]{:.2f}s".format(c, a, b, dur), end="")
    time.sleep(0.1)
print("\n"+"执行结束".center(scale//2, '-'))#上面一段代码结尾是end=”“，是不回车的，本行代码执行前要先回车

```

### 题目5：数字类型转换
获得用户输入的一个正整数输入，输出该数字对应的中文字符表示。0到9对应的中文字符分别是：零一二三四五六七八九

### 实现如下：

```
a = "零一二三四五六七八九十"
b = input()
for c in b:
    print(a[eval(c)],end='')
```

### 题目6：绘制风轮

### 实现如下：

```
import turtle                                        
                                                     
turtle.pencolor("black")                             
turtle.pensize(5)                                    
                                                     
turtle.seth(135)  #改变行进方向                            
turtle.fd(150)    #在当前方向前进150像素                      
turtle.left(90)   #左转90度                             
turtle.circle(150,45)  #半径150像素，画45度的圆               
turtle.goto(0,0)       #坐标回到起点                       
                                                     
turtle.seth(225)                                     
turtle.fd(150)                                       
turtle.left(90)                                      
turtle.circle(150,45)                                
turtle.goto(0,0)                                     
                                                     
turtle.seth(315)                                     
turtle.fd(150)                                       
turtle.left(90)                                      
turtle.circle(150,45)                                
turtle.goto(0,0)                                     
                                                     
turtle.seth(45)                                      
turtle.fd(150)                                       
turtle.left(90)                                      
turtle.circle(150,45)                                
turtle.goto(0,0)                                     
```

### 题目7:计算1~100的和

### 实现如下:

```
sum = 0
for x in range(101):
    sum = sum + x
print(sum)
```



