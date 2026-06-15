---
Difficulty: Easy
Topics: Linked Lists
---
# Remove Linked List Elements

This is a part of [[LeetCode Patterns]].

You are given the `head` of a linked list and an integer `val`, remove all the nodes of the linked list that has `Node.val == val`, and return the **new head**.

**Example 1:**

```java
Input: head = [2,1,4,1,2,3], val = 2

Output: [1,4,1,3]
```

**Example 2:**

```java
Input: head = [1,1], val = 1

Output: []
```

**Constraints:**

- `0 <= Length of the list <= 10,000`.
- `1 <= Node.val <= 50`
- `0 <= val <= 50`

**Solutions:**

```python
# Definition for singly-linked list.

# class ListNode:

#     def __init__(self, val=0, next=None):

#         self.val = val

#         self.next = next

class Solution:

    def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:

        prev, cur = None, head

  

        while cur and cur.val == val:

            head = head.next

            prev = cur

            cur = cur.next

        while cur:

            if cur.val == val:

                prev.next = cur.next

            else:

                prev = cur

            cur = cur.next

        return head
```

```python
# Definition for singly-linked list.

# class ListNode:

#     def __init__(self, val=0, next=None):

#         self.val = val

#         self.next = next

class Solution:

    def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:

        dummy = ListNode(-1, head)

        cur = dummy

  

        while cur.next:

            if cur.next.val == val:

                cur.next = cur.next.next

            else:

                cur = cur.next

        return dummy.next
```