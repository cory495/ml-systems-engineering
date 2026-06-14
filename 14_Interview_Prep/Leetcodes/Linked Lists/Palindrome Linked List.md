---
Difficulty: Easy
Topics: Linked Lists
---

# Palindrome Linked List

This is a part of [[LeetCode Patterns]].

You are given the `head` of a singly linked list, return `true` if it is a **palindrome** or `false` otherwise.

A **palindrome** is a sequence that reads the same forward and backward.

**Example 1:**

```java
Input: head = [1,2,3,2,1]

Output: true
```

**Example 2:**

```java
Input: head = [2,2]

Output: true
```

**Example 3:**

```java
Input: head = [2,1]

Output: false
```

**Constraints:**

- `1 <= Length of the list <= 100,000`.
- `0 <= Node.val <= 9`

**Follow up:** Could you do it in `O(n)` time and `O(1)` space?

**Solutions:**

```python
# Definition for singly-linked list.

# class ListNode:

#     def __init__(self, val=0, next=None):

#         self.val = val

#         self.next = next

class Solution:

    def isPalindrome(self, head: Optional[ListNode]) -> bool:

        stack = []

        cur = head

        while cur:

            stack.append(cur.val)

            cur = cur.next

        n = len(stack)

        for i in range(n // 2):

            if stack[i] != stack[n-i-1]:

                return False

        return True
```

```python
# Definition for singly-linked list.

# class ListNode:

#     def __init__(self, val=0, next=None):

#         self.val = val

#         self.next = next

class Solution:

    def isPalindrome(self, head: Optional[ListNode]) -> bool:

        fast = slow = head

  

        while fast and fast.next:

            fast = fast.next.next

            slow = slow.next

        prev = None

        while slow:

            tmp = slow.next

            slow.next = prev

            prev = slow

            slow = tmp

        while prev:

            if prev.val != head.val:

                return False

            prev = prev.next

            head = head.next

  

        return True
```