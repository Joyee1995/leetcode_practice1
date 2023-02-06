# [349. Intersection of Two Arrays](https://leetcode.com/problems/intersection-of-two-arrays/)

題目重點:
*本题就开始考虑 什么时候用set 什么时候用数组，本题其实是使用set的好题，但是后来力扣改了题目描述和 测试用例，添加了 0 <= nums1[i], nums2[i] <= 1000 条件，所以使用数组也可以了，不过建议大家忽略这个条件。 尝试去使用set。*

*那有同学可能问了，遇到哈希问题我直接都用set不就得了，用什么数组啊。直接使用set 不仅占用空间比数组大，而且速度要比数组慢，set把数值映射到key上都要做hash计算的。不要小瞧 这个耗时，在数据量大的情况，差距是很明显的。*



```python
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        tmp = set()
        result = set()
        for i in nums1:
            tmp.add(i)
        for j in nums2:
            if j in tmp:
                result.add(j)
        return result

        
```