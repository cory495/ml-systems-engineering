---
Difficulty: Medium
Topics: Backtracing
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - interview
  - programming
  - backtracing
Type: Interview
---
# Permutations

This is a part of [[LeetCode Patterns]].

Given an array `nums` of **unique** integers, return all the possible permutations. You may return the answer in **any order**.

**Example 1:**

```java
Input: nums = [1,2,3]

Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

**Example 2:**

```java
Input: nums = [7]

Output: [[7]]
```

**Constraints:**

- `1 <= nums.length <= 6`
- `-10 <= nums[i] <= 10`

**Solutions:**

```python
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        res = []
        n = len(nums)
        
        def backtrace(i, subset):
            if i == n:
                res.append(subset)
                return
            for j in range(i, n):
                new_subset = subset[::]
                new_subset[i], new_subset[j] = new_subset[j], new_subset[i]
                backtrace(i+1, new_subset)
        
        backtrace(0, nums)
        return res
```

```python
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        res = []
        n = len(nums)
        
        def backtrace(i):
            if i == n:
                res.append(nums[::])
                return
            for j in range(i, n):
                nums[i], nums[j] = nums[j], nums[i]
                backtrace(i+1)
                nums[i], nums[j] = nums[j], nums[i]
        
        backtrace(0)
        return res
```
