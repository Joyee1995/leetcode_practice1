# [151. Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/)

題目重點：
这里我还是提高一下本题的难度：不要使用辅助空间，空间复杂度要求为O(1)。
*以下python提交的code沒有符合*


以下提交的解題思路：
先把頭尾的空白去掉，然後紀錄substring，遇到空白就把substring寫進result，然後再用while檢查下一個char是不是空白

代碼隨想錄思路/看題解檢討：
先把前後中間多餘的空格去掉，然後reverse，遇到空白再reverse就可以達到 space O(1)

```python
class Solution:
    def reverseWords(self, s: str) -> str:
        result = ""
        substring = ""
        tmp = 0
        for j,l in enumerate(s):
            if l!=" ":
                tmp = j
                break
        s = s[tmp:]
        i = len(s)-1
        while i>=0:
            if s[i]!=" ":
                substring+=s[i]
            else:
                result+=substring[::-1]
                # if i==len(s)-1:
                #     result+=""
                # elif i==0:
                #     result+=""
                # el
                if substring!="":
                    print(result)
                    result+=" "
                while s[i-1]==" ":
                    i-=1
                substring = ""
            i-=1
        result+=substring[::-1]
        print(result)
        return result
```