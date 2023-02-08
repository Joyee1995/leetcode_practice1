# [15. 3Sum](https://leetcode.com/problems/3sum/)

題目重點：
*答案中不可以包含重复的三元组*
這裡用之前1_two_sum的方法再去重會超時、用python itertools.combination先找組合再去重也會超時。
用雙指針做比較適合



```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        result = []
        List=sorted(nums)
        print(nums)
        for i,j in enumerate(List):
            if (i>0 and List[i]==(List[i-1])):
                # 我们要做的是 不能有重复的三元组，但三元组内的元素是可以重复的！，所以這裡只能用List[i]==(List[i-1]，不能用List[i]==(List[i+1]
                continue
            left = i+1
            right = len(List)-1
            while (right>left):
                if (List[i]+List[left]+List[right])==0:
                    result.append([List[i],List[left],List[right]])
                    while (right>left and List[right]==List[right-1]):
                    # right去重
                        right-=1
                    while (right>left and List[left]==List[left+1]):
                    # left去重   
                        left+=1
                    right-=1
                    left+=1
                elif (List[i]+List[left]+List[right])>0:
                    right -= 1
                elif (List[i]+List[left]+List[right])<0:
                    left += 1
        return result
```