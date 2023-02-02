# [977. Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/)

題目重點：
理解雙指針

*Given an integer array nums sorted in non-decreasing order*
*trick:題目一開始就說明給予的是sort的array，所以新的list裡最大值一定是在左右兩側（負數平方後有可能比原本正數大*

```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        i=0
        #一個指針指最前面
        j=len(nums)-1
        #一個指針指最後面
        k=len(nums)-1
        #k是新list的index，從後面開始是已知最有兩側是最大，最小不明
        result = [0]*len(nums)
        #注意新list的初始化
        for _ in enumerate(nums):
            new_i = nums[i]*nums[i]
            new_j = nums[j]*nums[j]
            if new_i > new_j:
                result[k] = new_i
                i+=1
            else:
                result[k] = new_j
                j-=1
            k-=1
        return result
```