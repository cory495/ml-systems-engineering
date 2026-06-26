---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - interview
  - programming
Type: Interview
Topics: Trees
Difficulty: Easy
---
# Binary Tree Preorder Traversal

This is a part of [[LeetCode Patterns]].

You are given the `root` of a binary tree, return the **preorder traversal** of its nodes' values.

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/cbfdb2c1-2d7b-43e0-e6dc-426c90448200/public)

```java
Input: root = [1,2,3,4,5,6,7]

Output: [1,2,4,5,3,6,7]
```

**Example 2:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/7509d2ed-c696-40f3-98a3-2f635893c100/public)

```java
Input: root = [1,2,3,null,4,5,null]

Output: [1,2,4,3,5]
```

**Example 3:**

```java
Input: root = []

Output: []
```

**Constraints:**

- `0 <= number of nodes in the tree <= 100`
- `-100 <= Node.val <= 175`

**Follow up:** Recursive solution is trivial, could you do it iteratively?

**Solutions:**

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def preorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        res = []
        def dfs(node):
            if not node:
                return
            res.append(node.val)
            dfs(node.left)
            dfs(node.right)
        dfs(root)
        return res
```
