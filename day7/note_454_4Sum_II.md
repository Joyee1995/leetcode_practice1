# [454. 4Sum II](https://leetcode.com/problems/4sum-ii/)

題目重點：
使用map/dict降低時間複雜度，用空間換時間

*題目只要求要回傳幾個組合，沒有要列出！*

```python
class Solution:
    def fourSumCount(self, nums1: List[int], nums2: List[int], nums3: List[int], nums4: List[int]) -> int:
        cnt = 0
        tmp = dict()
        for i in nums1:
            for j in nums2:
                if (i+j) in tmp:
                    tmp[i+j] += 1
                else:
                    tmp[i+j] = 1
        
        for k in nums3:
            for l in nums4:
                if (0-(k+l)) in tmp:
                    cnt += tmp[0-(k+l)]
        return cnt

```