---
Difficulty: Hard
Topics: Trees
---
# Serialize and Deserialize Binary Tree

This is a part of [[LeetCode Patterns]].

Implement an algorithm to serialize and deserialize a binary tree.

Serialization is the process of converting an in-memory structure into a sequence of bits so that it can be stored or sent across a network to be reconstructed later in another computer environment.

You just need to ensure that a binary tree can be serialized to a string and this string can be deserialized to the original tree structure. There is no additional restriction on how your serialization/deserialization algorithm should work.

**Note:** The input/output format in the examples is the same as how NeetCode serializes a binary tree. You do not necessarily need to follow this format.

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/a9dfb17f-70e9-42a3-ba97-33cfd82f6100/public)

```java
Input: root = [1,2,3,null,null,4,5]

Output: [1,2,3,null,null,4,5]
```

**Example 2:**

```java
Input: root = []

Output: []
```

**Constraints:**

- `0 <= The number of nodes in the tree <= 1000`.
- `-1000 <= Node.val <= 1000`

**Solutions:**

```python
# Definition for a binary tree node.

# class TreeNode:

#     def __init__(self, val=0, left=None, right=None):

#         self.val = val

#         self.left = left

#         self.right = right

  

class Codec:

    # Encodes a tree to a single string.

    def serialize(self, root: Optional[TreeNode]) -> str:

        res = []

        def preorder(node):

            if not node:

                res.append("X")

                return

            res.append(str(node.val))

            preorder(node.left)

            preorder(node.right)

        preorder(root)

        return "#".join(res)

    # Decodes your encoded data to tree.

    def deserialize(self, data: str) -> Optional[TreeNode]:

        vals = data.split("#")

        i = 0

  

        def nav_preorder():

            nonlocal i

            if vals[i] == "X":

                i += 1

                return None

            node = TreeNode(int(vals[i]))

            i += 1

            node.left = nav_preorder()

            node.right = nav_preorder()

            return node

        return nav_preorder()
```