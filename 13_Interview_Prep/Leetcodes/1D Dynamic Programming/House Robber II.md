---
Difficulty: Medium
Topics: 1D Dynamic Programming
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - interview
  - programming
Type: Interview
---
# House Robber II

This is a part of [[LeetCode Patterns]].

You are given an integer array `nums` where `nums[i]` represents the amount of money the `i`th house has. The houses are arranged in a circle, i.e. the first house and the last house are neighbors.

You are planning to rob money from the houses, but you cannot rob **two adjacent houses** because the security system will automatically alert the police if two adjacent houses were _both_ broken into.

Return the _maximum_ amount of money you can rob **without** alerting the police.

**Example 1:**

```java
Input: nums = [3,4,3]

Output: 4
```

Explanation: You cannot rob `nums[0] + nums[2] = 6` because `nums[0]` and `nums[2]` are adjacent houses. The maximum you can rob is `nums[1] = 4`.

**Example 2:**

```java
Input: nums = [2,9,8,3,6]

Output: 15
```

Explanation: You cannot rob `nums[0] + nums[2] + nums[4] = 16` because `nums[0]` and `nums[4]` are adjacent houses. The maximum you can rob is `nums[1] + nums[4] = 15`.

**Constraints:**

- `1 <= nums.length <= 100`
- `0 <= nums[i] <= 200`


**Solutions:**
```python
class Solution:

    def rob(self, nums: List[int]) -> int:

        rob1, rob2 = 0, 0

  

        if len(nums) == 0:

            return 0

  

        if len(nums) == 1:

            return nums[0]

  

        for num in nums[:-1]:

            rob1, rob2 = rob2, max(num + rob1, rob2)

  

        rob3, rob4 = 0, 0

        for num in nums[1:]:

            rob3, rob4 = rob4, max(num + rob3, rob4)

        return max(rob2, rob4)
```

```python
class Solution:

    def rob(self, nums: List[int]) -> int:

  

        if len(nums) == 1:

            return nums[0]

        def rob_line(arr):

            prev = curr = 0

            for x in arr:

                prev, curr = curr, max(curr, prev + x)

            return curr

  

        return max(rob_line(nums[1:]), rob_line(nums[:-1]))
```