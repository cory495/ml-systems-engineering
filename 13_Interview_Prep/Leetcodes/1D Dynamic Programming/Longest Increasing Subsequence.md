---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - interview
  - programming
  - dynamic-programming
Type: Interview
Topics: 1D Dynamic Programming
Difficulty: Medium
---
# Longest Increasing Subsequence

This is a part of [[LeetCode Patterns]].

Given an integer array `nums`, return the _length_ of the longest strictly _increasing_ subsequence.

A **subsequence** is a sequence that can be derived from the given sequence by deleting some or no elements without changing the relative order of the remaining characters.

- For example, `"cat"` is a subsequence of `"crabt"`.

**Example 1:**

```java
Input: nums = [9,1,4,2,3,3,7]

Output: 4
```

Explanation: The longest increasing subsequence is [1,2,3,7], which has a length of 4.

**Example 2:**

```java
Input: nums = [0,3,1,3,2,3]

Output: 4
```

**Constraints:**

- `1 <= nums.length <= 1000`
- `-1000 <= nums[i] <= 1000`

**Solutions:**

```python
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        if not nums:
            return 0
        
        n = len(nums)
        dp = [1] * n
        
        for i in range(1, n):
            for j in range(i):
                if nums[j] < nums[i]:
                    dp[i] = max(dp[i], dp[j] + 1)
        
        return max(dp)
```

```python
import bisect

class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        tails = [] 
        
        for num in nums:
            pos = bisect.bisect_left(tails, num)
            if pos == len(tails):
                tails.append(num)
            else:
                tails[pos] = num
        
        return len(tails)
```
