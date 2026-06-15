---
Difficulty: Easy
Topics: Two Pointers
---
# Sort Array by Parity

This is a part of [[LeetCode Patterns]].

You are given an integer array `nums`, move all the even integers at the beginning of the array followed by all the odd integers.

Return **any array** that satisfies this condition.

**Example 1:**

```java
Input: nums = [3,1,2,4]

Output: [2,4,3,1]
```

Explanation: The outputs [4,2,3,1], [2,4,1,3], and [4,2,1,3] would also be accepted.

**Example 2:**

```java
Input: nums = [0]

Output: [0]
```

**Constraints:**

- `1 <= nums.length <= 5000`.
- `0 <= nums[i] <= 5000`.

**Solutions:**

```python
class Solution:

    def sortArrayByParity(self, nums: List[int]) -> List[int]:

        n = len(nums)

        i, j = 0, n-1

  

        res = [0]*n

        for num in nums:

            if num % 2 == 0:

                res[i] = num

                i += 1

            else:

                res[j] = num

                j -= 1

        return res
```

```python
class Solution:

    def sortArrayByParity(self, nums: List[int]) -> List[int]:

        i, j = 0, len(nums) - 1

  

        while i < j:

            if nums[i] % 2 > nums[j] % 2:

                nums[i], nums[j] = nums[j], nums[i]

  

            if nums[i] % 2 == 0:

                i += 1

  

            if nums[j] % 2 == 1:

                j -= 1

  

        return nums
```