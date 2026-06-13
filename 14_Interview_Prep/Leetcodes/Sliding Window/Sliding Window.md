# Sliding Window

## Core Idea
Sliding window is used to reduce nested loops by maintaining a window of elements and adjusting its boundaries dynamically.

---

## When to Use
Use sliding window when:
- subarray or substring problems
- longest / shortest / maximum / minimum conditions

---

## Types

### Fixed Size Window
Window size stays constant.

Example:
```python
window_sum = sum(nums[:k])
max_sum = window_sum

for i in range(k, len(nums)):
    window_sum += nums[i] - nums[i-k]
    max_sum = max(max_sum, window_sum)
```

---

### Variable Size Window
Window expands and contracts.

Example:
```python
left = 0
seen = set()

for right in range(len(s)):
    while s[right] in seen:
        seen.remove(s[left])
        left += 1
    seen.add(s[right])
```

---

## Key Insight
Brute force: O(n^2)
Sliding window: O(n)

---

## Template

```python
left = 0

for right in range(len(arr)):
    # expand window

    while invalid_condition:
        left += 1
```
---
## Relevant Problems
### Easy
- down:: [[Best Time to Buy and Sell Stock]]
- down:: [[Contain Duplicate II]]
### Medium
- down:: [[Longest Substring without Repeating Characters]]
- down:: [[Longest Repeating Character Replacement]]
- down:: [[Permutation in String]]
### Hard
- down:: [[Minimum Window Substring]]