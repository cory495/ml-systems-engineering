---
Difficulty: Medium
Topics: Trees
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - interview
  - programming
Type: Interview
---
# Valid Binary Search Tree

This is a part of [[LeetCode Patterns]].

Given the `root` of a binary tree, return `true` if it is a **valid binary search tree**, otherwise return `false`.

A **valid binary search tree** satisfies the following constraints:

- The left subtree of every node contains only nodes with keys **less than** the node's key.
- The right subtree of every node contains only nodes with keys **greater than** the node's key.
- Both the left and right subtrees are also binary search trees.

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/18f9a316-8dc2-4e11-d304-51204454ac00/public)

```java
Input: root = [2,1,3]

Output: true
```

**Example 2:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/6f14cb8d-efad-4221-2beb-fba2b19c8a00/public)

```java
Input: root = [1,2,3]

Output: false
```

Explanation: The root node's value is 1 but its left child's value is 2 which is greater than 1.

**Constraints:**

- `1 <= The number of nodes in the tree <= 1000`.
- `-1000 <= Node.val <= 1000`

**Solutions:**

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    def isValidBST(self, root: Optional[TreeNode], val_min = float('-inf'), val_max = float('inf')) -> bool:
        if not root:
            return True
        if val_min < root.val < val_max:
            return self.isValidBST(root.left, val_min, root.val) and self.isValidBST(root.right, root.val, val_max)
        else:
            return False
```
