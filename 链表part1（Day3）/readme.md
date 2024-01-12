# 链表
链表考虑虚拟头节点：虚拟头节点的定义
## 203. 移除链表元素
```python
class Solution:
    def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:
        
        root = ListNode(val=0, next=head)

        while root.next:
            if root.next.val == val:
                root.next = root.next.next
            else:
                root = root.next

        return head
```
## 707. 设计链表
```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class MyLinkedList:

    def __init__(self):
        self.size = 0
        self.dummy_head = ListNode()

    def get(self, index: int) -> int:
        if index < 0 or index >= self.size:
            return -1
        cur = self.dummy_head.next
        for i in range(index):
            cur = cur.next 
        return cur.val


    def addAtHead(self, val: int) -> None:
        self.dummy_head.next = ListNode(val, self.dummy_head.next)
        self.size += 1


    def addAtTail(self, val: int) -> None:
        cur = self.dummy_head
        for i in range(self.size):
            cur = cur.next
        cur.next = ListNode(val)
        self.size += 1

    def addAtIndex(self, index: int, val: int) -> None:
        if index < 0 or index > self.size:
            return
        cur = self.dummy_head
        for i in range(index):
            cur = cur.next
        cur.next = ListNode(val, cur.next)
        self.size += 1


    def deleteAtIndex(self, index: int) -> None:
        if index < 0 or index >= self.size:
            return 
        cur = self.dummy_head
        for i in range(index):
            cur = cur.next
        cur.next = cur.next.next
        self.size -= 1
```
## 206. 反转链表
依然类似于虚拟头节点，双指针
![image](https://github.com/GuozhengSui/Leetcode/assets/86645048/0430f793-a11f-4cf6-9296-b75e665682d0)


```python
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        cur  = head
        pre  =None
        while cur != None:
            temp = cur.next
            cur.next = pre
            pre = cur
            cur = temp
            
        return pre
```
