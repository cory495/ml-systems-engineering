---
Difficulty: Medium
Topics: Trees
---
# Kth Smallest Integer in BST

This is a part of [[LeetCode Patterns]].

Given the `root` of a binary search tree, and an integer `k`, return the `kth` smallest value (**1-indexed**) in the tree.

A **binary search tree** satisfies the following constraints:

- The left subtree of every node contains only nodes with keys **less than** the node's key.
- The right subtree of every node contains only nodes with keys **greater than** the node's key.
- Both the left and right subtrees are also binary search trees.

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/02eca3db-f72f-4277-7134-faec4f02e500/public)

```java
Input: root = [2,1,3], k = 1

Output: 1
```

**Example 2:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/dca6c42d-2327-4036-f7f2-3e99d8203100/public)

```java
Input: root = [4,3,5,2,null], k = 4

Output: 5
```

**Constraints:**

- `1 <= k <= The number of nodes in the tree <= 1000`.
- `0 <= Node.val <= 1000`

**Solutions:**

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    def kthSmallest(self, root: Optional[TreeNode], k: int) -> int:
        def in_order_creation(root):
            arr = []
            if root.left:
                arr.extend(in_order_creation(root.left))
            arr.append(root)
            if root.right:
                arr.extend(in_order_creation(root.right))
            return arr
        
        in_order = in_order_creation(root)
        return in_order[k-1].val
```

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    def kthSmallest(self, root: Optional[TreeNode], k: int) -> int:
        count = k
        res = root.val
        def dfs(root):
            nonlocal count, res

            if not root:
                return

            dfs(root.left)
            if count == 0:
                return
            count -= 1
            if count == 0:
                res = root.val
                return
            dfs(root.right)
        
        dfs(root)
        return res
```
