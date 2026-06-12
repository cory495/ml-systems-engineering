---
Difficulty: Easy
Topics: Arrays
---
# Max Consecutive Ones

You are given a binary array `nums`, return the maximum number of consecutive `1`'s in the array.

**Example 1:**

```java
Input: nums = [1,1,0,1,1,1]

Output: 3
```

  

**Example 2:**

```java
Input: nums = [1,0,1,1,0,1]

Output: 2
```

**Constraints:**

- `1 <= nums.length <= 100,000`
- `nums[i]` is either `0` or `1`.

**Solution:**

```python
class Solution:

    def findMaxConsecutiveOnes(self, nums: List[int]) -> int:

        count = 0

        max_count = 0

        for i in range(len(nums)):

            count += 1

            if nums[i] == 0:

                count = 0

            max_count = max(max_count, count)

        return max_count
```