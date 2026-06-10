```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        i = head

        if not i:
            return False

        j = head.next
        if not j:
            return False
        while True:
            if i is j:
                return True
            i = i.next
            j = j.next

            if (not i) or (not j):
                return False
            j = j.next
            if not j:
                return False
```
