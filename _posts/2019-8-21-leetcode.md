---
layout: post
title: LeetCode练习题
categories: [python]
description: some word here
keywords: keyword1, keyword2
---

### 题目一

给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。
你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。
示例:
给定 nums = [2, 7, 11, 15], target = 9
因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]


### 答案

```
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in nums:
            if int(i) == self:
                print(nums.index(i))
            else:
                continue

    if __name__ == '__main__':
        string = input("")
        nums = eval(string)
        print(nums)
        target = input("")
        # print(nums.index(target))
        self = int(target) - int(nums[0])

        twoSum(self, nums, target)
```


