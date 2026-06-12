---
Difficulty: Easy
Topics: Linked Lists
---
# Reverse Linked List

This is a part of [[LeetCode Patterns]].

Given the beginning of a singly linked list `head`, reverse the list, and return the new beginning of the list.

**Example 1:**

```java
Input: head = [0,1,2,3]

Output: [3,2,1,0]
```

**Example 2:**

```java
Input: head = []

Output: []
```

**Constraints:**

- `0 <= The length of the list <= 1000`.
- `-1000 <= Node.val <= 1000`

**Solutions:**

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
