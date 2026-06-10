---
Difficulty: Easy
Topics: Trees
---
# Same Binary Tree

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/4d811f95-0488-490b-1f4f-fc5489df0f00/public)

```java
Input: p = [1,2,3], q = [1,3,2]

Output: false
```

**Constraints:**

- `0 <= The number of nodes in both trees <= 100`.
- `-100 <= Node.val <= 100`
**Solutions:**

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    def isSameTree(self, p: Optional[TreeNode], q: Optional[TreeNode]) -> bool:
        if not p and not q:
            return True
        if not p or not q:
            return False
        
        return (p.val == q.val) and (self.isSameTree(p.left, q.left)) and (self.isSameTree(p.right, q.right))
```
