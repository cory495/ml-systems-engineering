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
