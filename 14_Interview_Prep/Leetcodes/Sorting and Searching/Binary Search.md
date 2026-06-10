---
Difficulty: Easy
Topics: Sorting
---

# Binary Search



You are given an array of **distinct** integers `nums`, sorted in ascending order, and an integer `target`.

Implement a function to search for `target` within `nums`. If it exists, then return its index, otherwise, return `-1`.

Your solution must run in O(logn)O(logn) time.

**Example 1:**

```java
Input: nums = [-1,0,2,4,6,8], target = 4

Output: 3
```

**Example 2:**

```java
Input: nums = [-1,0,2,4,6,8], target = 3

Output: -1
```

**Constraints:**

- `1 <= nums.length <= 10000`.
- `-10000 < nums[i], target < 10000`
- All the integers in `nums` are **unique**.

**Solutions**:
```python
class Solution:

    def search(self, nums: List[int], target: int) -> int:

        n = len(nums)

        l, r = 0, len(nums)-1

  

        while l <= r:

            mid = (l+r) // 2

            if nums[mid] == target:

                return mid

            if nums[mid] < target:

                l = mid + 1

            else:

                r = mid - 1

        return -1
```