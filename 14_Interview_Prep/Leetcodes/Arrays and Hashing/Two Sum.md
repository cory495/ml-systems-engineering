---
Difficulty: Easy
Topics: Arrays
---
# Two Sum

This is a part of [[LeetCode Patterns]].
Given an array of integers `nums` and an integer `target`, return the indices `i` and `j` such that `nums[i] + nums[j] == target` and `i != j`.

You may assume that _every_ input has exactly one pair of indices `i` and `j` that satisfy the condition.

Return the answer with the smaller index first.

**Example 1:**

```java
Input: 
nums = [3,4,5,6], target = 7

Output: [0,1]
```

Explanation: `nums[0] + nums[1] == 7`, so we return `[0, 1]`.

**Example 2:**

```java
Input: nums = [4,5,6], target = 10

Output: [0,2]
```

**Example 3:**

```java
Input: nums = [5,5], target = 10

Output: [0,1]
```

**Constraints:**

- `2 <= nums.length <= 1000`
- `-10,000,000 <= nums[i] <= 10,000,000`
- `-10,000,000 <= target <= 10,000,000`
- **Only one valid answer exists.**

**Solution**

```python
class Solution:

    def twoSum(self, nums: List[int], target: int) -> List[int]:

        for i in range(len(nums)):

            for j in range(i+1, len(nums)):

                if nums[i] + nums[j] == target:

                    return [i, j]
```

The initial solution runs in O(n) time. In order to achieve O(1) time, a different thought process must be done. A data structure is needed that can look up if a value exists in O(1) time and can easily view the index that the value is at. This leads directly to a dictionary. Then, the logic is arbitrary. Finally, edge cases must now be considered. What if `target=4`, but the array is `[2, 3, 6]`. Now, we have 2 at index 1. This means 2 can be selected twice if we do not directly state that one index cannot be chosen twice. This logic results in the following:
```python
class Solution:

    def twoSum(self, nums: List[int], target: int) -> List[int]:

        dt = {}

        for i in range(len(nums)):

            dt[nums[i]] = i

        for i in range(len(nums)):

            desired = target - nums[i]

            if dt.get(desired, -1) > -1 and i != dt.get(desired, -1):

                return [i, dt[desired]]
```