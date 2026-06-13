---
Difficulty: Easy
Topics: Two Pointers
---
# Move Zeroes

This is a part of [[LeetCode Patterns]].

You are given an integer array `nums`, move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.

**Note** that you must do this in-place without making a copy of the array.

**Example 1:**

```java
Input: nums = [0,0,1,2,0,5]

Output: [1,2,5,0,0,0]
```

**Example 2:**

```java
Input: nums = [0,1,0]

Output: [1,0,0]
```

**Constraints:**

- `1 <= nums.length <= 10,000`
- `-(2^31) <= nums[i] <= ((2^31)-1)`

**Follow up:** Could you minimize the total number of operations done?

**Solutions:**

```python
class Solution:

    def moveZeroes(self, nums: List[int]) -> None:

        """

        Do not return anything, modify nums in-place instead.

        """

        i = j = 0

        n = len(nums)

  

        while i < n and j < n:

            while j < n and nums[j] == 0:

                j += 1

            if j >= n:

                break

            nums[i] = nums[j]

            i += 1

            j += 1

        while i < n:

            nums[i] = 0

            i += 1
```

```python
class Solution:

    def moveZeroes(self, nums: List[int]) -> None:

        i = 0

  

        for j in range(len(nums)):

            if nums[j] != 0:

                nums[i] = nums[j]

                i += 1

  

        while i < len(nums):

            nums[i] = 0

            i += 1
```