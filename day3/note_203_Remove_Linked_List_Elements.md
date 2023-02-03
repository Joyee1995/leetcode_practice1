# [203. Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/)

題目重點：
了解虛擬頭的使用技巧

解題思路：
頭節點的刪除方式和其他節點不同，在traverse每個linked list的時候也卡卡的

最後提交
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:
        dummynode = ListNode(next=head)
        #為了讓所有節點刪除的方式具有一致性，所以創一個虛擬節點
        cur = dummynode
        while(cur.next!=None):
            if (cur.next.val==val):
                cur.next = cur.next.next
            else:
                cur = cur.next
        return dummynode.next
```