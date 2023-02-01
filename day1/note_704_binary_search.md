# [704. Binary Search](https://leetcode.com/problems/binary-search/)


[代碼隨想錄文章連結](https://programmercarl.com/0704.%E4%BA%8C%E5%88%86%E6%9F%A5%E6%89%BE.html)

題目重點：
熟悉左閉右閉，左閉右開兩種區間規則寫出來的二分法

解題思路：
*You must write an algorithm with O(log n) runtime complexity.*
條件限制不能用暴力解


```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left = 0
        right = len(nums) -1
        #注意區間，right assign成len(nums)-1即為左閉右閉
        while left<=right:
            #左閉右閉 left<=right的時候還是有意義
            middle = left+(right-left)//2
            #middle常常會搞混
            if nums[middle] > target:
                right = middle-1
                #左閉右閉也會影響right這裡
            elif nums[middle] < target:
                left = middle+1
            else:
                return middle
        return -1
```