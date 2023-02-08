# [383. Ransom Note](https://leetcode.com/problems/ransom-note)


看完題解檢討：
dict應該只紀錄magazine的，然後遍歷ransomnote時，直接減掉dict中的值，如果要ransomnote有的cha，magazine=0或沒有，就直接return false。

```python
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        dict_ransomNote = dict()
        dict_magazine = dict()
        for i in ransomNote:
            if i in dict_ransomNote:
                dict_ransomNote[i] += 1
            else :
                dict_ransomNote[i] = 1
        
        for j in magazine:
            if j in dict_magazine:
                dict_magazine[j] += 1
            else :
                dict_magazine[j] = 1
        
        for k in dict_ransomNote:
            if k not in dict_magazine:
                return False
            if dict_magazine[k] <dict_ransomNote[k]:
                return False
        return True        
```
