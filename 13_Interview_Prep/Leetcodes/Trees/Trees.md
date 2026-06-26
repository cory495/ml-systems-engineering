---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - interview
  - programming
Type: Interview
---
# Trees

## Core Idea
A tree is a hierarchical data structure consisting of nodes connected by edges. Each node can have child nodes, forming parent-child relationships.

---

## Key Properties
- Root node at the top.
- No cycles.
- Binary trees have at most two children.
- Height often determines complexity.
- Recursive structure makes DFS natural.

---

## Common Patterns

### 1. Depth-First Search (DFS)
Explore as far as possible before backtracking.

```python
def dfs(node):
    if not node:
        return

    dfs(node.left)
    dfs(node.right)
```

---

### 2. Breadth-First Search (BFS)
Explore level by level.

```python
queue = deque([root])
```

Uses a queue.

---

### 3. Tree Traversals

#### Preorder
```python
root -> left -> right
```

#### Inorder
```python
left -> root -> right
```

#### Postorder
```python
left -> right -> root
```

---

### 4. Recursive Divide and Conquer
Solve left and right subtrees independently.

Examples:
- Maximum Depth
- Diameter of Binary Tree
- Balanced Binary Tree

---

### 5. Binary Search Tree (BST)
Leverage ordering properties.

```python
left < root < right
```

Examples:
- Validate BST
- Lowest Common Ancestor
- Kth Smallest Element

---

## Complexity Cheat Sheet
- DFS: O(n)
- BFS: O(n)
- BST Search: O(log n) average
- BST Insert: O(log n) average
- BST Delete: O(log n) average

---

## Relevant Problems

### Easy
- down:: [[Invert Binary Trees]]
- down:: [[Maximum Depth of Binary Tree]]
- down:: [[Same Binary Tree]]
- down:: [[Subtree of Another Tree]]
- down:: [[Diameter of a Binary Tree]]
- down:: [[Binary Tree Inorder Traversal]]
- down:: [[Balanced Binary Tree]]
- down:: [[Binary Tree Postorder Traversal]]
- down:: [[Binary Tree Preorder Traversal]]
- down:: [[Binary Tree Inorder Traversal]]
### Medium
- down:: [[Count Good Nodes in Binary Tree]]
- down:: [[Kth Smallest Integer in BST]]
- down:: [[Validate Binary Search Tree]]
- down:: [[Binary Tree Level Order Traversal]]
- down:: [[Binary Tree Right Side View]]
- down:: [[Lowest Common Ancestor in Binary Search Tree]]
- down:: [[Construct Binary Tree from Preorder and Inorder Traversal]]
### Hard
- down:: [[Binary Tree Path Sum]]
- down:: [[Serialize and Deserialize Binary Tree]]