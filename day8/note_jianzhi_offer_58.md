# [剑指 Offer 58 - II. 左旋转字符串](https://leetcode.cn/problems/zuo-xuan-zhuan-zi-fu-chuan-lcof/)


題解感想：
除了substring的方法，只要前k個reverse，k:k=n做reverse，最後再整個str做reverse就可以達到一樣的效果

*一些同学热衷于使用substr，来做这道题。 其实使用substr 和 反转 时间复杂度是一样的 ，都是O(n)，但是使用substr申请了额外空间，所以空间复杂度是O(n)，而反转方法的空间复杂度是O(1)。*

如果想让这套题目有意义，就不要申请额外空间

```python
class Solution:
    def reverseLeftWords(self, s: str, n: int) -> str:
        substring = s[:n]
        tmp = s[n:]
        return tmp+substring
        # print(substring)
```