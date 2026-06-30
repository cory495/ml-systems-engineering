```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseBetween(self, head: Optional[ListNode], left: int, right: int) -> Optional[ListNode]:
        prev = dummy = ListNode(0, head)

        for _ in range(left - 1):
            prev = prev.next

        sublist_tail = sublist_head = prev.next
        for _ in range(right - left):
            sublist_tail = sublist_tail.next

        next_node = sublist_tail.next
        sublist_tail.next = None
        reversed_sublist = self.reverseList(sublist_head)
        prev.next = reversed_sublist
        sublist_head.next = next_node

        return dummy.next
        
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        prev, curr = None, head

        while curr:
            temp = curr.next
            curr.next = prev
            prev = curr
            curr = temp
        return prev
```

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseBetween(self, head: Optional[ListNode], left: int, right: int) -> Optional[ListNode]:
        dummy = ListNode(0, head)
        leftPrev, cur = dummy, head

        for _ in range(left - 1):
            leftPrev, cur = cur, cur.next

        prev = None
        for _ in range(right - left + 1):
            tmpNext = cur.next
            cur.next = prev
            prev, cur = cur, tmpNext

        leftPrev.next.next = cur
        leftPrev.next = prev

        return dummy.next
```
