---
Difficulty: Easy
Topics: 1D Dynamic Programming
---
# Min Climbing Stairs

This is a part of [[LeetCode Patterns]].

You are given an array of integers `cost` where `cost[i]` is the cost of taking a step from the `ith` floor of a staircase. After paying the cost, you can step to either the `(i + 1)th` floor or the `(i + 2)th` floor.

You may choose to start at the index `0` or the index `1` floor.

Return the minimum cost to reach the top of the staircase, i.e. just past the last index in `cost`.

**Example 1:**

```java
Input: cost = [1,2,3]

Output: 2
```

Explanation: We can start at index = `1` and pay the cost of `cost[1] = 2` and take two steps to reach the top. The total cost is `2`.

**Example 2:**

```java
Input: cost = [1,2,1,2,1,1,1]

Output: 4
```

Explanation: Start at index = `0`.

- Pay the cost of `cost[0] = 1` and take two steps to reach index = `2`.
- Pay the cost of `cost[2] = 1` and take two steps to reach index = `4`.
- Pay the cost of `cost[4] = 1` and take two steps to reach index = `6`.
- Pay the cost of `cost[6] = 1` and take one step to reach the top.
- The total cost is `4`.

**Constraints:**

- `2 <= cost.length <= 100`
- `0 <= cost[i] <= 100`

**Solutions:**

```python
class Solution:

    def minCostClimbingStairs(self, cost: List[int]) -> int:

        n = len(cost)

        steps = [0]*n

        if n == 0:

            return 0

        if n == 1:

            return cost[0]

        steps[0] = cost[0]

        steps[1] = cost[1]

        for i in range(2, n):

            steps[i] = min(steps[i-1], steps[i-2])+cost[i]

        return min(steps[-1], steps[-2])
```

```python
class Solution:

    def minCostClimbingStairs(self, cost: List[int]) -> int:

        n = len(cost)

        if n == 0:

            return 0

        if n == 1:

            return cost[0]

        prev0, prev1 = cost[0], cost[1]

        for i in range(2, n):

            cur = min(prev0, prev1) + cost[i]

            prev0, prev1 = prev1, cur

        return min(prev0, prev1)
```