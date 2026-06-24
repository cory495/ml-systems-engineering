---
Difficulty: Easy
Topics: Trees
---
# Diameter of Binary Tree

This is a part of [[LeetCode Patterns]].

The **diameter** of a binary tree is defined as the **length** of the longest path between _any two nodes within the tree_. The path does not necessarily have to pass through the root.

The **length** of a path between two nodes in a binary tree is the number of edges between the nodes. Note that the path can _not_ include the same node twice.

Given the root of a binary tree `root`, return the **diameter** of the tree.

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/90e1d7a0-4322-4c5d-c59b-dde2bf92bb00/public)

```java
Input: root = [1,null,2,3,4,5]

Output: 3
```

Explanation: 3 is the length of the path `[1,2,3,5]` or `[5,3,2,4]`.

**Example 2:**

```java
Input: root = [1,2,3]

Output: 2
```

**Constraints:**

- `1 <= number of nodes in the tree <= 100`
- `-100 <= Node.val <= 100`

**Solutions:**

```python
# Definition for a binary tree node.

# class TreeNode:

#     def __init__(self, val=0, left=None, right=None):

#         self.val = val

#         self.left = left

#         self.right = right

  

class Solution:

    def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:

        res = 0

        def dfs(root, height=0):

            nonlocal res

            if not root:

                return height

            left = dfs(root.left, height)

            right= dfs(root.right, height)

            res = max(res, left + right)

            return 1 + max(left, right)

        dfs(root)

        return res
```