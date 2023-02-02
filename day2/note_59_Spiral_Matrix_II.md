# [59. Spiral Matrix II](https://leetcode.com/problems/squares-of-a-sorted-array/)

題目重點：
熟悉區間定義

解題思路：
全部用左閉右開

```python
class Solution:
    def generateMatrix(self, n: int) -> List[List[int]]:
        nums = [[0] * n for _ in range(n)]
        startx = 0
        starty = 0
        cnt = 1
        offset = 1
        mid = n//2
        for _ in range(n//2):
            #n//2是跑的圈數
            for j in  range(startx,n-offset):
                #最上排，左到右
                nums[starty][j] = cnt
                cnt+=1
            for i in range(starty,n-offset):
                #最右排，上到下
                nums[i][n-offset] = cnt
                cnt+=1
            for jb in range(n-offset,startx,-1):
                #最下排，右到左
                nums[n-offset][jb] = cnt
                cnt+=1
            for ib in range(n-offset,starty,-1):
                #最左排，下到上
                nums[ib][startx] = cnt
                cnt+=1
            startx+=1
            starty+=1
            offset+=1
        if (n%2):
            nums[mid][mid] = cnt
        return nums

```