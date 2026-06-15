---
Difficulty: Easy
Topics: Arrays
---
# Contains Duplicate

This is a part of [[LeetCode Patterns]].

Given an integer array `nums`, return `true` if any value appears **more than once** in the array, otherwise return `false`.

**Example 1:**

```java
Input: nums = [1, 2, 3, 3]

Output: true
```

  

**Example 2:**

```java
Input: nums = [1, 2, 3, 4]

Output: false
```

**Constraints:**

- `0 <= nums.length <= 10^5`
- `-10^9 <= nums[i] <= 10^9`
**Solution:**

```python
class Solution:

    def hasDuplicate(self, nums: List[int]) -> bool:

        return len(set(nums)) != len(nums)
```
