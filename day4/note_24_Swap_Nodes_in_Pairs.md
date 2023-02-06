# [24. Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/)

題目重點：
while裡的條件建議畫圖理解再寫，否則很容易出現指針異常的error
*虛擬節點的應用*


```python
class Solution:
    def swapPairs(self, head: Optional[ListNode]) -> Optional[ListNode]:
        dummynode = ListNode(next=head)
        cur = dummynode
        while(cur.next and cur.next.next):
            tmp = cur.next
            tmp2 = cur.next.next.next
            #兩個tmp一定要先記錄起來
            cur.next = cur.next.next
            cur.next.next = tmp
            tmp.next = tmp2
            cur = cur.next.next
        return dummynode.next
```