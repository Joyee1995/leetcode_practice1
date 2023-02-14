# [239. Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)

題目重點：
使用自定義單調棧

做題感想：
發現自己對python的class還是沒有這麼熟悉

```python
class MyQueue():
    def __init__(self):
        self.queue = deque()
    
    def pop(self,value):
        if self.queue and value == self.queue[0]:
        # 因為如果要pop的元素會是window最前面的值，而如果最前面的值比較小，在push的時候就被刪掉了，所以只要比較最前面的element就好
            self.queue.popleft()

    def push(self,value):
        while self.queue and self.queue[-1]<value:
            self.queue.pop()
        self.queue.append(value)
    
    def getMax(self):
        return self.queue[0]



class Solution:
    def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:
        result = []
        queue = MyQueue()
        for i in range(k):
            queue.push(nums[i])
        # 先把最前面的k個element放進queue裡
        result.append(queue.getMax())
        for i in range(k,len(nums)):
            queue.pop(nums[i-k])
            queue.push(nums[i])
            result.append(queue.getMax())
        return result


```