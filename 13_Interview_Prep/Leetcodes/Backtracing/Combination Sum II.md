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
# Combination Sum II

This is a part of [[LeetCode Patterns]].

You are given an array of integers `candidates`, which may contain duplicates, and a target integer `target`. Your task is to return a list of all **unique combinations** of `candidates` where the chosen numbers sum to `target`.

Each element from `candidates` may be chosen **at most once** within a combination. The solution set must not contain duplicate combinations.

You may return the combinations in **any order** and the order of the numbers in each combination can be in **any order**.

**Example 1:**

```java
Input: candidates = [9,2,2,4,6,1,5], target = 8

Output: [
  [1,2,5],
  [2,2,4],
  [2,6]
]
```

**Example 2:**

```java
Input: candidates = [1,2,3,4,5], target = 7

Output: [
  [1,2,4],
  [2,5],
  [3,4]
]
```

**Constraints:**

- `1 <= candidates.length <= 100`
- `1 <= candidates[i] <= 50`
- `1 <= target <= 30`

**Solutions:**

```python
class Solution:
    def combinationSum2(self, candidates: List[int], target: int) -> List[List[int]]:
        res = []
        candidates = sorted(candidates)
        def backtrace(cur, left, tar):
            if tar < 0:
                return
            if tar == 0:
                res.append(cur)
                return
            
            for i in range(left, len(candidates)):
                if i > 0 and i-1 >= left and candidates[i] == candidates[i-1]:
                    continue
                backtrace(cur + [candidates[i]], i+1, tar - candidates[i])
        
        backtrace([], 0, target)
        return res
```
