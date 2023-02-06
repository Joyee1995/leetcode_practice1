# [142. Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/)


題目重點：
快慢指針的應用，如果有環，快慢指針一定會相遇，環的入口處-head的長度=相遇處-環的入口處

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        slow,fast = head,head
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            if slow==fast:
                index1 = head
                index2 = slow
                while index1!=index2:
                    index1 = index1.next
                    index2 = index2.next
                return index1
        return None
```