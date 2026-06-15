---
Difficulty: Medium
Topics: Arrays
---
# Majority Element II

This is a part of [[LeetCode Patterns]].

You are given an integer array `nums` of size `n`, find all elements that appear more than `⌊ n/3 ⌋` times. You can return the result in any order.

**Example 1:**

```java
Input: nums = [5,2,3,2,2,2,2,5,5,5]

Output: [2,5]
```

**Example 2:**

```java
Input: nums = [4,4,4,4,4]

Output: [4]
```

**Example 3:**

```java
Input: nums = [1,2,3]

Output: []
```

**Constraints:**

- `1 <= nums.length <= 50,000`.
- `-1,000,000,000 <= nums[i] <= 1,000,000,000`

**Follow up:** Could you solve the problem in linear time and in `O(1)` space?

**Solutions:**

```python
class Solution:
    def majorityElement(self, nums: List[int]) -> List[int]:
        goal_count = len(nums) //  3
        dt = {}

        for i in nums:
            dt[i] = dt.get(i, 0) + 1
        
        res = []
        for key, val in dt.items():
            if val > goal_count:
                res.append(key)
        return res
```

```python
class Solution:
    def majorityElement(self, nums: List[int]) -> List[int]:
        goal_count = len(nums) //  3
        dt = {}
        res = []

        for num in nums:
            dt[num] = dt.get(num, 0) + 1
            if dt[num] == goal_count + 1:
                res.append(num)
            if len(res) == 2:
                break
        return res
```
