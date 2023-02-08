# [剑指 Offer 05. 替换空格](https://leetcode.cn/problems/ti-huan-kong-ge-lcof/)



題目重點：
对于线性数据结构，填充或者删除，后序处理会高效的多。好好体会一下。

題解感想：
可以造python method2的方法試一下，在原本的str上做更動，省下space

*ps每次想要在原本的str上做操作都有一個奇怪的bug！！！要找出原因*

```python
class Solution:
    def replaceSpace(self, s: str) -> str:
        if s=="":
            return ""
        spacenum = s.count(' ')
        # 先算有多少空格
        result = list(s)
        for _ in range(spacenum*2):
            result.append(' ')
        # 再留空格的位子
        left = len(s)-1
        # 一個指向要加入的元素
        right = len(result)-1
        #一個指向加入新list的index
        print(s)
        print(result)
        print("left:",result[left])
        print("right:",result[right])
        while left>=0:
            if result[left]!=' ':
                result[right] = result[left]
                right-=1
            else:
                result[right-2:right+1] = ["%","2","0"]
                right-=3
            left-=1
        return "".join(result)               
```