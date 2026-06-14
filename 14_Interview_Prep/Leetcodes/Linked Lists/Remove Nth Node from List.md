---
Difficulty: Medium
Topics: Linked Lists
---
# Remove Nth Node From End of List

This is a part of [[LeetCode Patterns]].

Given the `head` of a linked list and an integer `n`, remove the `nth` node from the end of the list and return its head.

**Example 1:**

```java
Input: head = [1,2,3,4], n = 2

Output: [1,2,4]
```

**Example 2:**

```java
Input: head = [5], n = 1

Output: []
```

**Example 3:**

```java
Input: head = [1,2], n = 2

Output: [2]
```

**Constraints:**

- The number of nodes in the list is `sz`.
- `1 <= sz <= 30`
- `0 <= Node.val <= 100`
- `1 <= n <= sz`

**Solutions:**

```python
# Definition for singly-linked list.

# class ListNode:

#     def __init__(self, val=0, next=None):

#         self.val = val

#         self.next = next

  

class Solution:

    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:

        stack = []

        cur = head

  

        while cur:

            stack.append(cur)

            cur = cur.next

        size = len(stack)

        if size - n == 0:

            head = head.next

        elif n == 1:

            stack[-1*(n+1)].next = None

        else:

            stack[-1*(n+1)].next = stack[-1*(n-1)]

        return head
```

```python
# Definition for singly-linked list.

# class ListNode:

#     def __init__(self, val=0, next=None):

#         self.val = val

#         self.next = next

  

class Solution:

    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:

        dummy = ListNode(0, head)

        slow = fast = dummy

  

        for _ in range(n):

            fast = fast.next

  

        while fast.next:

            fast = fast.next

            slow = slow.next

        slow.next = slow.next.next

  

        return dummy.next
```