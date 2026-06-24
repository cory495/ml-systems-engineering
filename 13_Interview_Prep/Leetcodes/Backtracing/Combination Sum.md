---
Difficulty: Medium
Topics: Backtracing
---
# Combination Sum

This is a part of [[LeetCode Patterns]].

You are given an array of **distinct** integers `nums` and a target integer `target`. Your task is to return a list of all **unique combinations** of `nums` where the chosen numbers sum to `target`.

The **same** number may be chosen from `nums` an **unlimited number of times**. Two combinations are the same if the frequency of each of the chosen numbers is the same, otherwise they are different.

You may return the combinations in **any order** and the order of the numbers in each combination can be in **any order**.

**Example 1:**

```java
Input:
nums = [2,5,6,9]
target = 9

Output: [[2,2,5],[9]]
```

Explanation:  
2 + 2 + 5 = 9. We use 2 twice, and 5 once.  
9 = 9. We use 9 once.

**Example 2:**

```java
Input:
nums = [3,4,5]
target = 16

Output: [[3,3,3,3,4],[3,3,5,5],[4,4,4,4],[3,4,4,5]]
```

**Example 3:**

```java
Input:
nums = [3]
target = 5

Output: []
```

**Constraints:**

- All elements of `nums` are **distinct**.
- `1 <= nums.length <= 20`
- `2 <= nums[i] <= 30`
- `2 <= target <= 30`

**Solutions:**

```python
class Solution:
    def combinationSum(self, nums: List[int], target: int) -> List[List[int]]:
        res = []
        def backtrace(cur, vals, target):
            if target < 0:
                return
            if target == 0:
                res.append(cur)
                return
            
            for i in range(len(vals)):
                backtrace(cur + [vals[i]], vals[:i+1], target - vals[i])
        
        backtrace([], nums.copy(), target)
        return res
```
