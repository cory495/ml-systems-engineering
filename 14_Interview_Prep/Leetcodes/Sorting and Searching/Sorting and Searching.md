# Sorting & Searching

## Core Idea
Searching finds a target value within a collection. Sorting arranges elements into a specific order to make searching, processing, and comparisons more efficient.

---

## Key Properties
- Searching can be linear or logarithmic depending on the data structure.
- Sorting often improves later operations.
- Many algorithms use divide-and-conquer.
- Binary Search requires sorted data.

---

## Common Patterns

### 1. Linear Search
Scan through elements one by one.

```python
for x in arr:
    if x == target:
        return True
```

Time Complexity: O(n)

---

### 2. Binary Search
Used on sorted arrays.

```python
while l <= r:
    mid = (l + r) // 2
```

Time Complexity: O(log n)

---

### 3. Divide and Conquer
Break a problem into smaller subproblems.

Examples:
- Merge Sort
- Quick Sort
- Binary Search

---

### 4. Partitioning
Rearrange elements around a pivot.

Examples:
- Quick Sort
- Quick Select

---

### 5. Heap-Based Selection
Efficiently find largest/smallest elements.

Examples:
- Kth Largest Element
- Top K Frequent Elements

---

## Common Interview Problems
- Binary Search
- Search in Rotated Sorted Array
- Find Minimum in Rotated Sorted Array
- Kth Largest Element in an Array
- Median of Two Sorted Arrays

---

## Complexity Cheat Sheet

### Searching
- Linear Search: O(n)
- Binary Search: O(log n)

### Sorting
- Merge Sort: O(n log n)
- Quick Sort: O(n log n) average
- Heap Sort: O(n log n)
- Bubble Sort: O(n²)
- Insertion Sort: O(n²)

---

## Relevant Problems

### Easy
- down:: [[Binary Search]]
### Medium
- down:: [[Sort an Array]]
- down:: [[Search a 2D Matrix]]