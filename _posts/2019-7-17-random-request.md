---
layout: post
title: 随机32位ID，拼接URL并请求，验证返回结果和ID的关系
categories: [python，interface]
description: some word here
keywords: keyword1, keyword2
---

### 需求

服务端根据用户ID的首字母将用户三等分，每一份下发不同的json，

### 需求分析

任务分析：

1. 三等分的方法很多，假设是mod 3
2. 首字母是0,3,6,9,c,e下载json1
3. 首字母是1,4,7,a,d,f下载json2
4. 首字母是2,5,8,b,d下载json3
5. 寻找json1,json2,json3中不同的关键字

根据以上任务内容，需求拆分如下：

1. 随机生成32位用户ID
2. 用ID和基本的URL去拼接请求获得返回值，拿出返回值中的唯一项
3. 校验ID的首位和第二步获得的结果是否一致

### 分模块功能实现如下：

1. 随机生成32位ID

    ```
    import random
    x = 0
    while x < 2:
        id_list = []

        # 循环32次，每次在指定范围内得到一个随机数，将每次取到的数追加到列表中
        for i in range(31):
            random_result = random.choices(['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'a', 'b', 'c', 'd', 'e', 'f'])
            id_list.append(random_result[0])

        # 上面的数据存到了id_list中，再将列表转换成字符串
        id_string = ''.join(id_list)
        x = x + 1
        print(id_string)
    ```

2. 写死一个ID，使用urllib库进行请求

    ```
    from urllib.parse import urlencode
    import urllib.request
    import json
    import jsonpath

    id_string = "bf8ec083f831b1b7dcea6fb85131ade"
    url = "http://api.tools.boochat.cn/api/app_check_v2?"
    params = {"did" : id_string,
                "boundle_id" : "com.boo.facecam",
                "platform" : "android",
                "version" : "1.0.9"

    }

    url2 = url + urlencode(params)  #拼接URL
    print(url2)

    res = urllib.request.urlopen(url2) #发起请求

    data = res.read()                  #把请求的返回值读到data中
    print(data)

    jsonData = json.loads(data, encoding='utf-8') #获取请求的返回值
    print(jsonData['code'])

    s = jsonpath.jsonpath(jsonData, '$..normal')  # 取到返回值中key叫normal的value。不管有多少层，写两个.都能取到
    print(s)
    ```

3. 写死一个ID，使用request库进行请求

    ```
    import jsonpath
    from urllib.parse import urlencode
    import requests

    id_string = "bf8ec083f831b1b7dcea6fb85131ade"
    url = "http://api.tools.boochat.cn/api/app_check_v2?"
    params = {"did" : id_string,
                "boundle_id" : "com.boo.facecam",
                "platform" : "android",
                "version" : "1.0.9"
    }

    url2 = url + urlencode(params)  #拼接URL
    print(url2)

    res = requests.get(url2)        #发起请求

    print(res.status_code)  #打印请求的返回值
    print(res.text)         #以文本形式打印网页源码
    print(res.content)      #以字节流形式打印返回值
    print(res.url)          #打印请求URL
    print(res.headers)      #打印头信息

    data = res.content

    jsonData = res.json()                           #解析json
    # jsonData = json.loads(data, encoding='utf-8') #解析json,和上面的方法效果一样
    print(jsonData['code'])

    s = jsonpath.jsonpath(jsonData, '$..normal')  # 取到返回值中key叫normal的value。不管有多少层，写两个.都能取到
    print(s)
    ```

4. 可优化部分：函数封装

    ### 完整代码如下：

    ```
    import jsonpath
    from urllib.parse import urlencode
    import requests
    import random


    def id_random():
        x = 0
        while x < 1:
            id_list = []
            # 循环32次，每次在指定范围内得到一个随机数，将每次取到的数追加到列表中
            for i in range(31):
                random_result = random.choices(['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'a', 'b', 'c', 'd', 'e', 'f'])
                id_list.append(random_result[0])
            # 上面的数据存到了id_list中，再将列表转换成字符串
            did = ''.join(id_list)
            print(did)
            print(did[0])
            if int(did[0], 16) % 3 == 0:
                print("A方案")
            elif int(did[0], 16) % 3 == 1:
                print("B方案")
            else:
                print("C方案")
            return did
        
        
    def new_url():
        url = "http://api.tools.boochat.cn/api/app_check_v2?"
        params = {"did" : id_random(),
                    "boundle_id" : "com.boo.facecam",
                    "platform" : "android",
                    "version" : "1.0.9"
        }
        url2 = url + urlencode(params)  #拼接URL
        res = requests.get(url2)        #发起请求
        jsonData = res.json()                           #解析json
        s = jsonpath.jsonpath(jsonData, '$..normal')  # 取到返回值中key叫normal的value。不管有多少层，写两个.都能取到
        return s


    if __name__ == '__main__':
        new_url()
    ```


