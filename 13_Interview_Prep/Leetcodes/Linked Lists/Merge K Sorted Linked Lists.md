---
Difficulty: Hard
Topics: Linked Lists
---
# Merge K Sorted Linked Lists

This is a part of [[LeetCode Patterns]].

You are given an array of `k` linked lists `lists`, where each list is sorted in ascending order.

Return the **sorted** linked list that is the result of merging all of the individual linked lists.

**Example 1:**

```java
Input: lists = [[1,2,4],[1,3,5],[3,6]]

Output: [1,1,2,3,3,4,5,6]
```

**Example 2:**

```java
Input: lists = []

Output: []
```

**Example 3:**

```java
Input: lists = [[]]

Output: []
```

**Constraints:**

- `0 <= lists.length <= 1000`
- `0 <= lists[i].length <= 100`
- `-1000 <= lists[i][j] <= 1000`

**Solutions:**

```python
# Definition for singly-linked list.

# class ListNode:

#     def __init__(self, val=0, next=None):

#         self.val = val

#         self.next = next

  

class Solution:    

    def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:

        dummy = cur = ListNode(0)

  

        while True:

            min_val, idx = float('inf'), -1

            for i, l in enumerate(lists):

                if l:

                    if l.val < min_val:

                        min_val = l.val

                        idx = i

            if idx == -1:

                break

            lists[idx] = lists[idx].next

            cur.next = ListNode(min_val)

            cur = cur.next

        return dummy.next
```

```python
class Solution:

    def mergeKLists(self, lists):

        heap = []

        for i, node in enumerate(lists):

            if node:

                heapq.heappush(heap, (node.val, i, node))

        dummy = cur = ListNode(0)

        while heap:

            _, i, node = heapq.heappop(heap)

            cur.next = node

            cur = cur.next

            if node.next:

                heapq.heappush(heap, (node.next.val, i, node.next))

        return dummy.next
```