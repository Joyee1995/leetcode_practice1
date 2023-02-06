# [242. Valid Anagram](https://leetcode.com/problems/valid-anagram/)

題目重點:
*什么时候想到用哈希法，当我们遇到了要快速判断一个元素是否出现集合里的时候，就要考虑哈希法。  这句话很重要，大家在做哈希表题目都要思考这句话。*
體驗list作為hash帶來的便利。

解題思路：
除了list，也可以用dict 



```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        record_s = [0]*26
        record_t = [0]*26
        print(ord('s')-ord('a'))
        for i in s:
            record_s[ord(i)-ord('a')]+=1
        for j in t:
            record_t[ord(j)-ord('a')]+=1
        if record_s==record_t:
            return True
        else:
            return False
```