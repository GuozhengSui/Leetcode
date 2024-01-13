虚拟头节点和双指针，快慢指针是链表问题的主要解决方法。
## 24. 两两交换链表中的节点
虚拟头节点
```python
class Solution:
    def swapPairs(self, head: Optional[ListNode]) -> Optional[ListNode]:
        dummy_head= ListNode(0, head)
        cur = dummy_head
        while cur.next != None and cur.next.next != None:
            temp = cur.next
            temp2 = cur.next.next.next

            cur.next = cur.next.next
            cur.next.next = temp
            cur.next.next.next = temp2

            cur = cur.next.next

        return dummy_head.next
```
## 19. 删除链表的倒数第 N 个结点
快慢指针
```python
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        dummmy_head = ListNode(0, head)
        fast = slow = dummmy_head
        for i in range(n+1):
            fast = fast.next
        while fast != None:
            fast = fast.next
            slow = slow.next
        slow.next = slow.next.next
        return dummmy_head.next
```
## 面试题 02.07. 链表相交
```python
class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> ListNode:
        lenA, lenB = 0, 0
        cur = headA
        while cur:
            lenA += 1
            cur = cur.next    

        cur = headB
        while cur:
            lenB += 1
            cur = cur.next


        if lenA > lenB:
            for i in range(lenA-lenB):
                headA = headA.next
        elif lenA < lenB:
            for i in range(lenB-lenA):
                headB = headB.next
        while headA:
            if headA == headB:
                return headA
            headA = headA.next
            headB = headB.next
        return None
```
## 142. 环形链表 II
数学问题，使用快慢指针
```python
class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        slow, fast = head, head
        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next
            if fast == slow:
                fast = head
                while fast != slow:
                    fast = fast.next
                    slow = slow.next
                return fast
        return None
```
