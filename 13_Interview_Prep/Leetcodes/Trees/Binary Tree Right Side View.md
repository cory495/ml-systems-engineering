---
Difficulty: Medium
Topics: Trees
---
# Binary Tree Right Side View

You are given the `root` of a binary tree. Return only the values of the nodes that are visible from the right side of the tree, ordered from top to bottom.

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/10f2e260-d7a8-4f46-a685-a7de5afd6d00/public)

```java
Input: root = [1,2,3,null,4,null,5]

Output: [1,3,5]
```

**Example 2:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/df99b5b2-a3b4-44a0-227d-5bb9ca6fd600/public)

```java
Input: root = [1,2,3,4,null,null,null,5]

Output: [1,3,4,5]
```

**Example 3:**

```java
Input: root = [1,null,2]

Output: [1,2]
```

**Example 4:**

```java
Input: root = []

Output: []
```

  

**Constraints:**

- `0 <= number of nodes in the tree <= 100`
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

    def rightSideView(self, root: Optional[TreeNode]) -> List[int]:

        res = []

  

        def lookAtNodes(root, depth=0):

            nonlocal res

  

            if not root:

                return

  

            if len(res) == depth:

                res.append(root.val)

            lookAtNodes(root.right, depth+1)

            lookAtNodes(root.left, depth+1)

            return

        lookAtNodes(root)

        return res
```