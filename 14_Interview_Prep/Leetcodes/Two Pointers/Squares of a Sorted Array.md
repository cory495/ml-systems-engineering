---
Topics: Two Pointers
Difficulty: Easy
---
# Squares of a Sorted Array

This is a part of [[LeetCode Patterns]].

You are given an integer array `nums` sorted in **non-decreasing** order, return an array of the **squares of each number** sorted in non-decreasing order.

**Example 1:**

```java
Input: nums = [-4,-1,0,3,10]

Output: [0,1,9,16,100]
```

Explanation: After squaring, the array becomes [16,1,0,9,100].  
After sorting, it becomes [0,1,9,16,100].

**Example 2:**

```java
Input: nums = [-7,-3,2,3,11]

Output: [4,9,9,49,121]
```

**Constraints:**

- `1 <= nums.length <= 10,000`
- `-10,000 <= nums[i] <= 10,000`
- `nums` is sorted in **non-decreasing** order.

**Follow up:** Squaring each element and sorting the new array is very trivial, could you find an `O(n)` solution using a different approach?

**Solutions:**

```python
class Solution:

    def sortedSquares(self, nums: List[int]) -> List[int]:

        n = len(nums)

        i, j = 0, n-1

        res = [0] * n

  

        for k in reversed(range(n)):

            if abs(nums[i]) > abs(nums[j]):

                res[k] = nums[i]*nums[i]

                i += 1

            else:

                res[k] = nums[j]*nums[j]

                j -= 1

        return res
```