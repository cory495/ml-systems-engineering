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

## Common Interview Problems
- Maximum Depth of Binary Tree
- Same Tree
- Invert Binary Tree
- Diameter of Binary Tree
- Balanced Binary Tree
- Binary Tree Level Order Traversal
- Validate Binary Search Tree

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