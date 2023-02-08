# [541. Reverse String II](https://leetcode.com/problems/reverse-string-ii/)

題解感想：
解題思路差不多，但沒有多用一個str/list，*要多練習*


```python
class Solution:
    def reverseStr(self, s: str, k: int) -> str:
        result = list()
        for i in range(0,len(s),k*2):
            substring = s[i:(i+k*2)]
            subsubstring =  substring[:k]
            subsubstring = subsubstring[::-1]
            substringend = substring[k:]
            print(subsubstring)
            print(substringend)
            new = subsubstring+substringend
            result.extend(new)
        return ''.join(result)
```