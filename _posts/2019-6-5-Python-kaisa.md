---
layout: post
title: 《python 语言程序设计》练习题之凯撒密码
categories: [python]
description: some word here
keywords: keyword1, keyword2
---

### 题目：凯撒密码

恺撒密码是古罗马恺撒大帝用来对军事情报进行加解密的算法，它采用了替换方法对信息中的每一个英文字符循环替换为字母表序列中该字符后面的第三个字符，即，字母表的对应关系如下：‪‬‪‬‪‬‪‬‪‬‮‬‪‬‫‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‫‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‮‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‫‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‮‬

原文：A B C D E F G H I J K L M N O P Q R S T U V W X Y Z‪‬‪‬‪‬‪‬‪‬‮‬‪‬‫‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‫‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‮‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‫‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‮‬

密文：D E F G H I J K L M N O P Q R S T U V W X Y Z A B C‪‬‪‬‪‬‪‬‪‬‮‬‪‬‫‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‫‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‮‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‫‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‮‬

对于原文字符P，其密文字符C满足如下条件：C=(P+3) mod 26‪‬‪‬‪‬‪‬‪‬‮‬‪‬‫‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‫‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‮‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‫‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‮‬

上述是凯撒密码的加密方法，解密方法反之，即：P=(C-3) mod 26‪‬‪‬‪‬‪‬‪‬‮‬‪‬‫‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‫‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‮‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‫‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‮‬

假设用户可能使用的输入包含大小写字母a~zA~Z、空格和特殊符号，请编写一个程序，对输入字符串进行恺撒密码加密，直接输出结果，其中空格不用进行加密处理。使用input()获得输入。


### 实现如下：

```
input = input("")
characterStr1 = "abcdefghijklmnopqrstuvwxyz"
characterStr2 = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"

for i in range(len(input)):
    pos = characterStr1.find(input[i])
    if pos != -1:
        if pos < 23:
            character = characterStr1[pos + 3]
            print(character, end="")
        elif pos > 23:
            character = characterStr1[pos - 23]
            print(character, end="")
        elif pos == 23:
            character = characterStr1[pos - 23]
            print(character, end="")
    else:
        pos = characterStr2.find(input[i])
        if pos != -1:
            if pos < 23:
                character = characterStr2[pos + 3]
                print(character, end="")
            elif pos > 23:
                character = characterStr2[pos - 23]
                print(character, end="")
            elif pos == 23:
                character = characterStr2[pos - 23]
                print(character, end="")
        else:
            print(input[i], end="")
```
### 优化如下：

```
input = input("")
characterStr1 = "abcdefghijklmnopqrstuvwxyz"
characterStr2 = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"

for i in range(len(input)):
    pos = characterStr1.find(input[i])
    if pos != -1:
        c = (pos + 3) % 26
        print(characterStr1[c], end="")
    else:
        pos = characterStr2.find(input[i])
        if pos != -1:
            c = (pos + 3) % 26
            print(characterStr2[c], end="")
        else:
            print(input[i], end="")
```

