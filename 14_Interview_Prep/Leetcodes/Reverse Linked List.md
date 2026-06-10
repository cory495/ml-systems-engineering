```python
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        dummy = None
        while head:
            next_node = head.next
            head.next = dummy
            dummy = head
            head = next_node
        return dummy
````
