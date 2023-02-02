# [209. Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)

題目重點：
理解滑动窗口,用雙指針實現滑動窗口

## 1. 暴力解
用兩層for循環遍歷每個可能
```python
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        result = float('INF')
        #要記得python的最大值
        for i,_ in enumerate(nums):
            sum = 0
            for j in range(i,len(nums)):
                sum += nums[j]
                if sum>=target:
                    sublen = j-i+1
                    print(sublen)
                    result = sublen if (sublen<result) else result
        return result if (result != float('INF')) else 0
```
時間複雜度：O(n)
*注意：暴力解在leetcode上不能通過，會超時*

## 2. 滑動窗口
用一層for解決題目
*要先想清楚for用的index是作為終止位置or起始位置*

```python
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        j = 0
        sum = 0
        result = float('INF')
        for i in range(len(nums)):
            sum += nums[i]
            while (sum>=target):
                sublen = i-j+1
                result = min(sublen,result)
                sum -= nums[j]
                j += 1
        return result if (result!=float('INF')) else 0
```

*雖然一層for一層while 但是時間複雜度是O(n)*

