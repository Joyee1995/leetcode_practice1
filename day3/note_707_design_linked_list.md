# [707. Design Linked List](https://leetcode.com/problems/design-linked-list)

題目重點：
考察链表综合操作的题目，練練虛擬頭


解題思路：
*一開始寫沒有虛擬頭的解法，寫得很卡，後來卡很多在遍歷的方式*

*以下tmp的initialize的地方要多多注意（複習要特別看），有時候initialize時，會用self.head next,有時候用self.head*

**TODO 要再補上tmp initialize的規則**




```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next


class MyLinkedList:

    def __init__(self):
        self.len = 0
        self.head = ListNode()

        
    def get(self, index: int) -> int:
        if (index <0 or index>=self.len):
            return -1
        else:
            tmp = self.head.next
            while index:
                tmp = tmp.next
                index-=1
            # for i in range(index):
            #     tmp = tmp.next
            
            return tmp.val
        
    
    def addAtHead(self, val: int) -> None:
        tmp = ListNode(val=val)
        tmp.next = self.head.next
        self.head.next = tmp
        self.len += 1
        

    def addAtTail(self, val: int) -> None:
        new_node = ListNode(val=val)
        tmp = self.head
        while (tmp.next!=None):
            tmp = tmp.next
        tmp.next = new_node
        self.len += 1
        

    def addAtIndex(self, index: int, val: int) -> None:
        if index <= 0:
            self.addAtHead(val)
            return
        elif index>self.len:
            return
        elif (index==self.len):
            self.addAtTail(val)
            return
        
        else:
            new_node = ListNode(val=val)
            tmp = self.head
            while index:
                tmp = tmp.next
                index-=1
            # for i in range(index):
            #     tmp = tmp.next
            new_node.next = tmp.next
            tmp.next = new_node
            self.len += 1



    def deleteAtIndex(self, index: int) -> None:
        if index<0 or index>=self.len:
            return
        # cur = self.head.next
        prev = self.head
        while index:
            # cur = cur.next
            prev = prev.next
            index-=1
        # for i in range(index):
        #     cur = cur.next
        #     prev = prev.next
        prev.next = prev.next.next
        self.len -= 1
        


# Your MyLinkedList object will be instantiated and called as such:
# obj = MyLinkedList()
# param_1 = obj.get(index)
# obj.addAtHead(val)
# obj.addAtTail(val)
# obj.addAtIndex(index,val)
# obj.deleteAtIndex(index)
```