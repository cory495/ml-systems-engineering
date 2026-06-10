---
Difficulty: Easy
Topics: Linked Lists
---
# Merge Two Sorted Linked Lists

You are given the heads of two sorted linked lists `list1` and `list2`.

Merge the two lists into one **sorted** linked list and return the head of the new sorted linked list.

The new list should be made up of nodes from `list1` and `list2`.

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/51adfea9-493a-4abb-ece7-fbb359d1c800/public)

```java
Input: list1 = [1,2,4], list2 = [1,3,5]

Output: [1,1,2,3,4,5]
```

**Example 2:**

```java
Input: list1 = [], list2 = [1,2]

Output: [1,2]
```

**Example 3:**

```java
Input: list1 = [], list2 = []

Output: []
```

**Constraints:**

- `0 <= The length of the each list <= 100`.
- `-100 <= Node.val <= 100`

**Solutions:**

```python
# Definition for singly-linked list.

# class ListNode:

#     def __init__(self, val=0, next=None):

#         self.val = val

#         self.next = next

  

class Solution:

    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:

        dummy = ListNode(0)

        cur = dummy

        while list1 or list2:

            if not list1:

                cur.next = list2

                return dummy.next

            if not list2:

                cur.next = list1

                return dummy.next

            if list1.val < list2.val:

                cur.next = list1

                cur = cur.next

                list1 = list1.next

            else:

                cur.next = list2

                cur = cur.next

                list2 = list2.next

        return dummy.next
```