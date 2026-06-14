---
Difficulty: Easy
Topics: Linked Lists
---

# Remove Duplicates from Sorted Array

This is a part of [[LeetCode Patterns]].

Given the `head` of a sorted linked list, _delete all duplicates such that each element appears only once_. Return _the linked list **sorted** as well_.

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/01/04/list1.jpg)

**Input:** head = [1,1,2]
**Output:** [1,2]

**Example 2:**

![](https://assets.leetcode.com/uploads/2021/01/04/list2.jpg)

**Input:** head = [1,1,2,3,3]
**Output:** [1,2,3]

**Constraints:**

- The number of nodes in the list is in the range `[0, 300]`.
- `-100 <= Node.val <= 100`
- The list is guaranteed to be **sorted** in ascending order.

**Solutions:**
```python
# Definition for singly-linked list.

# class ListNode:

#     def __init__(self, val=0, next=None):

#         self.val = val

#         self.next = next

class Solution:

    def deleteDuplicates(self, head: Optional[ListNode]) -> Optional[ListNode]:

        cur = head

  

        while cur and cur.next:

            if cur.val == cur.next.val:

                cur.next = cur.next.next

            else:

                cur = cur.next

        return head
```