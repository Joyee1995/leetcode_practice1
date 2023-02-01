# [27. Remove Element](https://leetcode.com/problems/remove-element/)

## 1. 暴力解

[代碼隨想錄文章連結](https://programmercarl.com/0027.%E7%A7%BB%E9%99%A4%E5%85%83%E7%B4%A0.html#_27-%E7%A7%BB%E9%99%A4%E5%85%83%E7%B4%A0)

題目重點：
雙指針法，快慢指針

解題思路：
不熟悉快慢指針，先用暴力法嘗試
邊traverse邊刪，因從前面刪list index會亂掉，所以從後面開始刪

*Do not allocate extra space for another array. You must do this by modifying the input array in-place with O(1) extra memory.*

暴力解
```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        cnt = 0
        if val in nums:
            for i, e in reversed(list(enumerate(nums))):
                #不熟悉python reverse traverse list
                if e==val:
                    cnt+=1
                    nums.pop(i)
                    #時間複雜度是O(n)
        return len(nums)
```
看影片後感想：
-  如果題目是可以用一行庫函數(library)解決的，就要意識道題目不是要考我們這個

## 2. 雙指針法

解題思路：
快指針：新list需要的元素
慢指針：新list更新的index

```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        slow = 0
        # cnt = 0
        #從slow就可以知道最後有幾個element
        for i,j in enumerate(nums):
            #i就是所謂的快指針
            #當是val的時候就繼續往下走
            #不是的話就assign給慢指針
            if j!=val:
                # cnt+=1
                nums[slow] = j
                slow+=1
        return slow
```







