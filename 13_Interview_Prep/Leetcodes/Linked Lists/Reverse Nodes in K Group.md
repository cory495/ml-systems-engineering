---
Difficulty: Hard
Topics: Linked Lists
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - interview
  - programming
Type: Interview
---
# Reverse Nodes in K-Group

This is a part of [[LeetCode Patterns]].

You are given the head of a singly linked list `head` and a positive integer `k`.

You must reverse the first `k` nodes in the linked list, and then reverse the next `k` nodes, and so on. If there are fewer than `k` nodes left, leave the nodes as they are.

Return the modified list after reversing the nodes in each group of `k`.

You are only allowed to modify the nodes' `next` pointers, not the values of the nodes.

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/67cf2fff-f20a-4558-6091-c3e857f56e00/public)

```java
Input: head = [1,2,3,4,5,6], k = 3

Output: [3,2,1,6,5,4]
```

**Example 2:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/af843e59-df12-4c55-652b-6ddab0a92900/public)

```java
Input: head = [1,2,3,4,5], k = 3

Output: [3,2,1,4,5]
```

**Constraints:**

- The length of the linked list is `n`.
- `1 <= k <= n <= 100`
- `0 <= Node.val <= 100`

**Solutions:**

```python
class Solution:

    def reverseKGroup(self, head, k):

        def get_kth(node, k):

            while node and k > 0:

                node = node.next

                k -= 1

            return node

  

        group_prev = dummy = ListNode(0, head)

  

        while True:

            kth = get_kth(group_prev, k)

            if not kth:

                break

  

            group_next = kth.next

  

            # reverse group

            prev, cur = kth.next, group_prev.next

  

            while cur != group_next:

                tmp = cur.next

                cur.next = prev

                prev = cur

                cur = tmp

  

            tmp = group_prev.next

            group_prev.next = kth

            group_prev = tmp

  

        return dummy.next
```