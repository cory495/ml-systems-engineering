# Two Pointers

## Definition

Two pointers is a technique where you use two indices (pointers) to traverse a data structure (usually an array or string) in a coordinated way.

Instead of using nested loops (O(n²)), you reduce work to O(n) by moving pointers strategically.

---

## When to Use Two Pointers

Use this pattern when you see:
- Searching from both ends (left/right)
- Comparing elements in a sorted array
- Palindromes / symmetry problems
- Removing duplicates in-place
- Pair-sum problems (sorted arrays)
- Partitioning or filtering in-place

---

## Core Variants

### A. Opposite Ends (Left + Right)

Used for:
- Palindrome checks
- Sorted pair problems
- Reverse / symmetry logic

```python
l = 0
r = len(arr) - 1

while l < r:
    if condition_met(arr[l], arr[r]):
        pass
    l += 1
    r -= 1
```

---

### B. Same Direction (Fast + Slow)

Used for:
- Removing duplicates
- Linked list cycle detection
- Compressing arrays

```python
slow = 0

for fast in range(len(arr)):
    if valid(arr[fast]):
        arr[slow] = arr[fast]
        slow += 1
```

---

### C. [[Sliding Window ]](Advanced Two Pointers)

Used for:
- Subarrays / substrings
- Maximum/minimum window problems

```python
l = 0

for r in range(len(arr)):
    add(arr[r])

    while invalid_window():
        remove(arr[l])
        l += 1
```

---

## Example: Palindrome Check

```python
def isPalindrome(s: str) -> bool:
    l, r = 0, len(s) - 1

    while l < r:
        while l < r and not s[l].isalnum():
            l += 1
        while l < r and not s[r].isalnum():
            r -= 1

        if s[l].lower() != s[r].lower():
            return False

        l += 1
        r -= 1

    return True
```

---

## Example: Sorted Two-Sum

```python
def twoSumSorted(nums, target):
    l, r = 0, len(nums) - 1

    while l < r:
        total = nums[l] + nums[r]

        if total == target:
            return [l, r]
        elif total < target:
            l += 1
        else:
            r -= 1
```

---

## Why It Works

| Approach       | Time Complexity |
|----------------|----------------|
| Brute force    | O(n^2)          |
| Two pointers   | O(n)            |

Each element is visited at most once per pointer.

---

## Common Mistakes

- Not moving pointers correctly
- Off-by-one errors (l < r vs l <= r)
- Using two pointers on unsorted data when ordering matters
- Forgetting edge cases (empty/single element)

---

## Mental Model

Two pointers = controlled scanning that avoids reprocessing work by coordinating movement instead of brute force comparison.

---

## Summary

Two pointers is a linear-time optimization technique for problems involving arrays/strings where structure allows bidirectional or coordinated traversal.

---
## Relevant Problems
### Easy
- down:: [[Valid Palindrome]]