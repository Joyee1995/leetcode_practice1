# [160. Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/)

題目重點：
同樣的val不代表同樣的node，intersection需要同樣的node

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> Optional[ListNode]:
        lenA = 0
        curA = headA
        while curA:
            lenA+=1
            curA = curA.next
        lenB = 0
        curB = headB
        while curB:
            lenB+=1
            curB = curB.next
        curA = headA
        curB = headB

        if lenA>lenB:
            lenA,lenB = lenB,lenA
            curA,curB = curB,curA

        for i in range(lenB-lenA):
            # 要先讓兩個linkedlist一樣長才可以比較
            curB = curB.next
        
        while curB and curA:
            if curB==curA:
                return curB
            else:
                curB = curB.next
                curA = curA.next
        return None
        
```