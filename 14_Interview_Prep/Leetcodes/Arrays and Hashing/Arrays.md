# Arrays

## Core Idea
An array is a contiguous block of memory that stores elements in indexed order. It allows O(1) access by index but has tradeoffs for insertion and deletion.

---

## Key Properties
- Fixed or dynamic size (Python lists are dynamic arrays)
- O(1) random access: arr[i]
- O(n) insert/delete (worst case due to shifting)

---

## Common Patterns

### 1. Traversal
- Iterate through all elements
- Used in most basic problems

---

### 2. Prefix Sum
Used to answer range sum queries efficiently.

```python
prefix[i] = sum(arr[0:i])
```

Range sum:
```python
prefix[r] - prefix[l-1]
```

---

### 3. [[Two Pointers]]
Used when array is sorted or needs pairing.

Examples:
- Two Sum (sorted)
- Container With Most Water
- Remove duplicates

---

### 4. In-place Modification
Modify array without extra space.

Examples:
- Move zeroes
- Remove element
- Rotate array

---

### 5. Partitioning
Split array into segments.

Examples:
- QuickSort partition logic
- Dutch National Flag problem

---

## Common Interview Problems
- Two Sum
- Best Time to Buy/Sell Stock
- Product of Array Except Self
- Maximum Subarray (Kadane’s Algorithm)

---

## Complexity Cheat Sheet
- Access: O(1)
- Search: O(n)
- Insert (middle): O(n)
- Delete (middle): O(n)

---
## Relevant Problems
### Easy
- down:: [[Contains Duplicate]]
- down:: [[Two Sum]]
- down:: [[Valid Anagram]]
### Medium
- down:: [[Group Anagrams]]
- down:: [[Top K Frequent Elements]]