---
Difficulty: Hard
Topics: Trees
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - interview
  - programming
Type: Interview
---
# Binary Tree Maximum Path Sum

This is a part of [[LeetCode Patterns]].

Given the `root` of a _non-empty_ binary tree, return the maximum **path sum** of any _non-empty_ path.

A **path** in a binary tree is a sequence of nodes where each pair of adjacent nodes has an edge connecting them. A node can _not_ appear in the sequence more than once. The path does _not_ necessarily need to include the root.

The **path sum** of a path is the sum of the node's values in the path.

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/9896b041-9021-44c2-ab3e-5cff76adf100/public)

```java
Input: root = [1,2,3]

Output: 6
```

Explanation: The path is 2 -> 1 -> 3 with a sum of 2 + 1 + 3 = 6.

**Example 2:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/19ce1187-387e-4323-f2c9-1a317ab36200/public)

```java
Input: root = [-15,10,20,null,null,15,5,-5]

Output: 40
```

Explanation: The path is 15 -> 20 -> 5 with a sum of 15 + 20 + 5 = 40.

**Constraints:**

- `1 <= The number of nodes in the tree <= 1000`.
- `-1000 <= Node.val <= 1000`

**Solutions

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    def maxPathSum(self, root: Optional[TreeNode]) -> int:
        max_sum = float('-inf')
        def dfs(root):
            nonlocal max_sum
            if not root:
                return 0
            
            left_gain = max(0, dfs(root.left))
            right_gain = max(0, dfs(root.right))

            max_sum = max(max_sum, root.val+left_gain+right_gain)
            return max(left_gain,right_gain) + root.val
        dfs(root)
        return max_sum
```
