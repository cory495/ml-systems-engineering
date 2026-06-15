---
Difficulty: Easy
Topics: Linked Lists
---
# Middle of the Linked List

This is a part of [[LeetCode Patterns]].

You are given the `head` of a singly linked list, return the **middle node** of the linked list.

If there are two middle nodes, return the **second middle node**.

**Example 1:**

```java
Input: head = [1,2,3,4,5]

Output: [3,4,5]
```

**Example 2:**

```java
Input: head = [1,2,3,4,5,6]

Output: [4,5,6]
```

**Constraints:**

- `1 <= The length of the list <= 100`
- `1 <= Node.val <= 100`

**Solutions:**

```python
# Definition for singly-linked list.

# class ListNode:

#     def __init__(self, val=0, next=None):

#         self.val = val

#         self.next = next

class Solution:

    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:

        slow = fast = head

  

        while fast and fast.next:

            fast = fast.next.next

            slow = slow.next

  

        return slow
```