# [1. Two Sum](https://leetcode.com/problems/two-sum/)

題目重點：
*本题其实有四个重点：*
- 为什么会想到用哈希表
- 哈希表为什么用map
- 本题map是用来存什么的
- map中的key和value用来存什么的


解題思路：
看到twosum會先想到加法，但想到減法，就會很容易想到用hash

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        tmp = dict()
        for i,j in enumerate(nums):
            tmp[j] = i
        
        result = []
        for j,i in enumerate(nums):
            if (target-i) in tmp:
                if (tmp[(target-i)]!=j):
                    result.extend([j,tmp[(target-i)]])
                    return result
        
```