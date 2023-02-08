# [18. 4Sum](https://leetcode.com/problems/4sum/)

題目重點：
和15類似，但這裡是4sum==target，break條件要注意一下（list裡面有負數）

*而454.四数相加II (opens new window)是四个独立的数组，只要找到A[i] + B[j] + C[k] + D[l] = 0就可以，不用考虑有重复的四个元素相加等于0的情况，所以相对于本题还是简单了不少！*

```python
class Solution:
    def fourSum(self, nums: List[int], target: int) -> List[List[int]]:
        result = []
        nums = sorted(nums)
        # print("nums:",nums)
        for i,_ in enumerate(nums):
            # print("i:",i)
            # print("i:",nums[i])
            if nums[i]>target and target>=0:
                break
            if i>0 and nums[i]==nums[i-1]:
                continue
            for j in range(i+1,len(nums)):
                # print("j:",j)
                # print("j:",nums[j])
                if nums[i]+nums[j]>target and target>=0:
                    break
                if j>i+1 and nums[j]==nums[j-1]:
                    continue
                left = j+1
                right = len(nums)-1
                while(right>left):
                    # print("total len",len(nums))
                    # print("i,j,left,right",i,j,left,right)
                    # print("i,j,left,right",nums[i],nums[j],nums[left],nums[right])
                    if (nums[i]+nums[j]+nums[left]+nums[right])==target:
                        # print("hihi")
                        result.append([nums[i],nums[j],nums[left],nums[right]])
                        while (right>left and nums[right]==nums[right-1]):
                            right-=1
                        while (right>left and nums[left]==nums[left+1]):
                            left+=1
                        right-=1
                        left+=1
                    elif (nums[i]+nums[j]+nums[left]+nums[right])<target:
                        left+=1
                    elif (nums[i]+nums[j]+nums[left]+nums[right])>target:
                        right-=1
                    
        return result
```
