---
Difficulty: Easy
Topics: Arrays
---
# Majority Element

This is a part of [[LeetCode Patterns]].

Given an array `nums` of size `n`, return the **majority element**.

The majority element is the element that appears more than `⌊n / 2⌋` times in the array. You may assume that the majority element always exists in the array.

**Example 1:**

```java
Input: nums = [5,5,1,1,1,5,5]

Output: 5
```

**Example 2:**

```java
Input: nums = [2,2,2]

Output: 2
```

**Constraints:**

- `1 <= nums.length <= 50,000`
- `-1,000,000,000 <= nums[i] <= 1,000,000,000`

**Follow-up:** Could you solve the problem in linear time and in `O(1)` space?

**Solutions:**

```python
class Solution:

    def majorityElement(self, nums: List[int]) -> int:

        dt = {}

        n = len(nums)

        for num in nums:

            dt[num] = dt.get(num, 0) + 1

            if dt[num] > n // 2:

                return num
```

```python
class Solution:

    def majorityElement(self, nums: List[int]) -> int:

        candidate = None

        count = 0

  

        for num in nums:

            if count == 0:

                candidate = num

  

            if num == candidate:

                count += 1

            else:

                count -= 1

  

        return candidate
```