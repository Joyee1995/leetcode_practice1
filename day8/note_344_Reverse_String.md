# [344. Reverse String](https://leetcode.com/problems/reverse-string/)


解題重點：
考察 reverse 函数的实现，同时也明确一下 平时刷题什么时候用 库函数，什么时候 不用库函数 


```python
class Solution:
    def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """
        left = 0
        right = len(s)-1
        while right>left:
            tmp = s[right]
            s[right] = s[left]
            s[left] = tmp
            right -= 1
            left += 1
```
