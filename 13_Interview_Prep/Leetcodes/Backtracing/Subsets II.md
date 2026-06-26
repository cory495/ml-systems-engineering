---
Difficulty: Medium
Topics: Backtracing
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - interview
  - programming
Type: Interview
---
# Subsets II

This is a part of [[LeetCode Patterns]].

You are given an array `nums` of integers, which may contain duplicates. Return all possible subsets.

The solution must **not** contain duplicate subsets. You may return the solution in **any order**.

**Example 1:**

```java
Input: nums = [1,2,1]

Output: [[],[1],[1,2],[1,1],[1,2,1],[2]]
```

**Example 2:**

```java
Input: nums = [7,7]

Output: [[],[7], [7,7]]
```

**Constraints:**

- `1 <= nums.length <= 11`
- `-20 <= nums[i] <= 20`

**Solutions:**

```python
class Solution:
    def subsetsWithDup(self, nums: List[int]) -> List[List[int]]:
        res = []
        nums.sort()

        def dfs(i, subset):
            if i == len(nums):
                res.append(subset[::])
                return

            subset.append(nums[i])
            dfs(i+1, subset)
            subset.pop()
            
            while i < len(nums)-1 and nums[i] == nums[i+1]:
                i += 1
            dfs(i+1, subset)

        dfs(0, [])
        return res
```
