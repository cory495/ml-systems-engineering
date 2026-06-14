---
Difficulty: Medium
Topics: Linked Lists
---
# Find the Duplicate Number

You are given an array of integers `nums` containing `n + 1` integers. Each integer in `nums` is in the range `[1, n]` inclusive.

There is exactly **one repeated integer** in `nums`, and every other integer appears at most once.

Return the repeated integer.

**Example 1:**

```java
Input: nums = [1,2,3,2,2]

Output: 2
```

**Example 2:**

```java
Input: nums = [1,2,3,4,4]

Output: 4
```

Follow-up: Can you solve the problem **without** modifying the array `nums` and using O(1)O(1) extra space?

**Constraints:**

- `1 <= n <= 10,000`
- `nums.length == n + 1`
- `1 <= nums[i] <= n`

**Solutions:**
```python
class Solution:

    def findDuplicate(self, nums: List[int]) -> int:

        for num in nums:

            idx = abs(num) - 1

            if nums[idx] < 0 :

                return abs(num)

            nums[idx] *= -1

        return -1
```