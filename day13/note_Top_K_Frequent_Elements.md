# [347. Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)

題目重點：
minheap的使用

做題後感想：
沒使用過python的heapq，不熟要怎麼push tuple

```python
import heapq
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        map = dict()
        for i in range(len(nums)):
            map[nums[i]] = map.get(nums[i],0)+1
            #map.get用法要記起來！
        
        priorityq = []
        for key,value in map.items():
            heapq.heappush(priorityq,(value,key))
            #value 是priority key，所以要放前面
            if len(priorityq)>k:
                heapq.heappop(priorityq)
        print(priorityq)
        result = []
        for i in range(k-1,-1,-1):
            value,key = priorityq.pop()
            result.append(key)
            #result = [0]*k
            # result[i] = heapq.heappop(priorityq)[1]
            #用下面標註的方法可能比append快一點點
        return result

```