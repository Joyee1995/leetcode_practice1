# [19. Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

題目重點：
要刪除第n個節點，需要traverse到n-1個節點

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        sz = 0
        cur = head
        while cur:
            sz+=1
            cur = cur.next
        print(sz)
        if n>sz:
            return
        delete_index = sz-n
        dummynode = ListNode(next=head)
        cur = dummynode
        for _ in range(delete_index):
            cur = cur.next
        cur.next = cur.next.next
        return dummynode.next
        
```