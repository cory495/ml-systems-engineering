---
Difficulty: Easy
Topics: 1D Dynamic Programming
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - interview
  - programming
  - dynamic-programming
Type: Interview
---
# Climbing Stairs

This is a part of [[LeetCode Patterns]].

You are given an integer `n` representing the number of steps to reach the top of a staircase. You can climb with either `1` or `2` steps at a time.

Return the number of distinct ways to climb to the top of the staircase.

**Example 1:**

```java
Input: n = 2

Output: 2
```

Explanation:

1. `1 + 1 = 2`
2. `2 = 2`

**Example 2:**

```java
Input: n = 3

Output: 3
```

Explanation:

1. `1 + 1 + 1 = 3`
2. `1 + 2 = 3`
3. `2 + 1 = 3`

**Constraints:**

- `1 <= n <= 45`

**Solutions:**

```python
class Solution:

    def climbStairs(self, n: int) -> int:

        if n == 1:

            return 1

        nums = [0]*n

        nums[0] = 1

        nums[1] = 2

        for i in range(2,n):

            nums[i] = nums[i-1]+nums[i-2]

        return nums[-1]
```

```python
class Solution:

    def climbStairs(self, n: int) -> int:

        if n == 1:

            return 1

        prev0 = 1

        prev1 = 2

        for i in range(2,n):

            prev0, prev1 = prev1, prev0+prev1

        return prev1
```