# Linked Lists

## Core Idea
A linked list stores elements as nodes connected through pointers. Each node contains a value and a reference to the next node.

---

## Key Properties
- Dynamic size.
- Sequential access only.
- O(1) insertion/deletion with node reference.
- No contiguous memory requirement.

---

## Common Patterns

### 1. Traversal
Move node by node.

```python
curr = head

while curr:
    curr = curr.next
```

---

### 2. Fast & Slow Pointers
Use two pointers moving at different speeds.

Examples:
- Detect Cycle
- Find Middle Node
- Happy Number

---

### 3. Reversal
Reverse pointers in-place.

```python
prev = None
curr = head
```

Examples:
- Reverse Linked List
- Reverse Nodes in K Group

---

### 4. Dummy Node
Simplifies edge cases involving the head.

```python
dummy = ListNode(0, head)
```

Examples:
- Remove Nth Node From End
- Merge Two Sorted Lists

---

### 5. Merge Lists
Combine multiple sorted linked lists.

Examples:
- Merge Two Sorted Lists
- Merge K Sorted Lists

---

## Common Interview Problems
- Reverse Linked List
- Linked List Cycle
- Merge Two Sorted Lists
- Reorder List
- Remove Nth Node From End of List
- Copy List with Random Pointer

---

## Complexity Cheat Sheet
- Access: O(n)
- Search: O(n)
- Insert at Head: O(1)
- Delete Given Node: O(1)

---

## Relevant Problems

### Easy
- down:: [[Reverse Linked List]]
- down:: [[Linked List Cycle Detection]]
- down:: [[Merge Two Sorted Linked Lists]]
