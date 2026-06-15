---
Difficulty: Medium
Topics: 1D Dynamic Programming
---
# House Robbers

This is a part of [[LeetCode Patterns]].

You are given an integer array `nums` where `nums[i]` represents the amount of money the `i`th house has. The houses are arranged in a straight line, i.e. the `i`th house is the neighbor of the `(i-1)`th and `(i+1)`th house.

You are planning to rob money from the houses, but you cannot rob **two adjacent houses** because the security system will automatically alert the police if two adjacent houses were _both_ broken into.

Return the _maximum_ amount of money you can rob **without** alerting the police.

**Example 1:**

```java
Input: nums = [1,1,3,3]

Output: 4
```

Explanation: `nums[0] + nums[2] = 1 + 3 = 4`.

**Example 2:**

```java
Input: nums = [2,9,8,3,6]

Output: 16
```

Explanation: `nums[0] + nums[2] + nums[4] = 2 + 8 + 6 = 16`.

**Constraints:**

- `1 <= nums.length <= 100`
- `0 <= nums[i] <= 100`

**Solutions:**

```python
class Solution:

    def rob(self, nums: List[int]) -> int:

        n = len(nums)

        if n == 0:

            return 0

        if n == 1:

            return nums[0]

  

        return max(nums[0] + self.rob(nums[2:]), self.rob(nums[1:]))
```

```python
class Solution:

    def rob(self, nums: List[int]) -> int:

        rob1, rob2 = 0, 0

  

        for num in nums:

            rob1, rob2 = rob2, max(num + rob1, rob2)

        return rob2
```