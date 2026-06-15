---
Difficulty: Medium
Topics: Linked Lists
---
# Add Two Numbers

This is a part of [[LeetCode Patterns]].

You are given two **non-empty** linked lists, `l1` and `l2`, where each represents a non-negative integer.

The digits are stored in **reverse order**, e.g. the number 321 is represented as `1 -> 2 -> 3 ->` in the linked list.

Each of the nodes contains a single digit. You may assume the two numbers do not contain any leading zero, except the number `0` itself.

Return the sum of the two numbers as a linked list.

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/fee72e19-6a21-45a5-365e-3cb45aba9700/public)

```java
Input: l1 = [1,2,3], l2 = [4,5,6]

Output: [5,7,9]

Explanation: 321 + 654 = 975.
```

**Example 2:**

```java
Input: l1 = [9], l2 = [9]

Output: [8,1]
```

**Constraints:**

- `1 <= l1.length, l2.length <= 100`.
- `0 <= Node.val <= 9`

**Solutions:**
```python
# Definition for singly-linked list.

# class ListNode:

#     def __init__(self, val=0, next=None):

#         self.val = val

#         self.next = next

  

class Solution:

    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:

        cur = dummy = ListNode(0)

  

        carry = 0

        while l1 and l2:

            val = l1.val + l2.val + carry

            carry, ones = math.floor(val / 10), val % 10

            cur.next = ListNode(ones)

            l1 = l1.next

            l2 = l2.next

            cur = cur.next

        while l1:

            val = l1.val + carry

            carry, ones = math.floor(val / 10), val % 10

            cur.next = ListNode(ones)

            l1 = l1.next

            cur = cur.next

        while l2:

            val = l2.val + carry

            carry, ones = math.floor(val / 10), val % 10

            cur.next = ListNode(ones)

            l2 = l2.next

            cur = cur.next

        if carry > 0:

            cur.next = ListNode(carry)

        return dummy.next
```

```python
# Definition for singly-linked list.

# class ListNode:

#     def __init__(self, val=0, next=None):

#         self.val = val

#         self.next = next

  

class Solution:

    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:

        cur = dummy = ListNode(0)

  

        carry = 0

        while l1 or l2 or carry:

            v1 = l1.val if l1 else 0

            v2 = l2.val if l2 else 0

            val = v1 + v2 + carry

            carry, ones = val // 10, val % 10

  

            cur.next = ListNode(ones)

            cur = cur.next

  

            if l1: l1 = l1.next

            if l2: l2 = l2.next

        return dummy.next
```