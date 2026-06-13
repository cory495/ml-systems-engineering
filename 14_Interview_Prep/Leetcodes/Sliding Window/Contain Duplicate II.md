---
Difficulty: Easy
Topics: Sliding Window
---

# Contains Duplicate II

This is a part of [[LeetCode Patterns]].

You are given an integer array `nums` and an integer `k`, return `true` if there are **two distinct indices** `i` and `j` in the array such that `nums[i] == nums[j]` and `abs(i - j) <= k`, otherwise return `false`.

**Example 1:**

```java
Input: nums = [1,2,3,1], k = 3

Output: true
```

**Example 2:**

```java
Input: nums = [2,1,2], k = 1

Output: false
```

**Constraints:**

- `1 <= nums.length <= 100,000`
- `-1,000,000,000 <= nums[i] <= 1,000,000,000`
- `0 <= k <= 100,000`


**Solutions:**

```python
class Solution:
    def containsNearbyDuplicate(self, nums: List[int], k: int) -> bool:
        left = right = 0
        vals = set()
        while right < len(nums):
            if len(vals) > k:
                vals.remove(nums[left])
                left += 1
            if nums[right] in vals:
                return True
            vals.add(nums[right])
            right += 1
        return False
```
