---
Difficulty: Medium
Topics: Arrays
---
# Longest Consecutive Sequence

This is a part of [[LeetCode Patterns]].
Given an array of integers `nums`, return _the length_ of the longest consecutive sequence of elements that can be formed.

A _consecutive sequence_ is a sequence of elements in which each element is exactly `1` greater than the previous element. The elements do _not_ have to be consecutive in the original array.

You must write an algorithm that runs in `O(n)` time.

**Example 1:**

```java
Input: nums = [2,20,4,10,3,4,5]

Output: 4
```

Explanation: The longest consecutive sequence is `[2, 3, 4, 5]`.

**Example 2:**

```java
Input: nums = [0,3,2,5,4,6,1,1]

Output: 7
```

**Constraints:**

- `0 <= nums.length <= 1000`
- `-10^9 <= nums[i] <= 10^9`

**Solutions:**

```python
class Solution:

    def longestConsecutive(self, nums: List[int]) -> int:

        n_set = set(nums)

        max_count = 1

        count = 1

        if len(nums) == 0:

            return 0

        for n in nums:

            if n-1 not in n_set:

                offset = 1

                while n+offset in n_set:

                    count += 1

                    offset += 1

                    max_count = max(max_count, count)

                count = 1

        return max_count
```

A slight improvement was made. Instead of iterating over the list `nums`, I iterated over the set `n_set`. This made it so that repeats were not considered, saving time drastically.
```python
class Solution:

    def longestConsecutive(self, nums: List[int]) -> int:

        n_set = set(nums)

        max_count = 1

        count = 1

        if len(nums) == 0:

            return 0

        for n in n_set:

            if n-1 not in n_set:

                offset = 1

                while n+offset in n_set:

                    count += 1

                    offset += 1

                    max_count = max(max_count, count)

                count = 1

        return max_count
```