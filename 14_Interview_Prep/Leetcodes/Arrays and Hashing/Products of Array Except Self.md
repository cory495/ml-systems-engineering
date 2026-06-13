---
Difficulty: Medium
Topics: Arrays
---

# Products of Array Except Self

This is a part of [[LeetCode Patterns]].

Given an integer array `nums`, return an array `output` where `output[i]` is the product of all the elements of `nums` except `nums[i]`.

Each product is **guaranteed** to fit in a **32-bit** integer.

Follow-up: Could you solve it in O(n)O(n) time without using the division operation?

**Example 1:**

```java
Input: nums = [1,2,4,6]

Output: [48,24,12,8]
```

**Example 2:**

```java
Input: nums = [-1,0,1,2,3]

Output: [0,-6,0,0,0]
```

**Constraints:**

- `2 <= nums.length <= 1000`
- `-20 <= nums[i] <= 20`\

**Solutions:**
```python
class Solution:

    def productExceptSelf(self, nums: List[int]) -> List[int]:

        ans = [1]*len(nums)

        for i in range(len(nums)):

            for j in range(len(nums)):

                if i != j:

                    ans[i] *= nums[j]

        return ans
```

The naive solution was to brute force the answer. The smarter idea was to use prefix and postfix together. This idea came naturally after doing a few of the multiplications by hand.
```python
class Solution:

    def productExceptSelf(self, nums: List[int]) -> List[int]:

        n = len(nums)

        prefix = [1]*n

        postfix = [1]*n

  

        for i in range(1, n):

            prefix[i] *= prefix[i-1] * nums[i-1]

        for i in range(n - 2, -1, -1):

            postfix[i] = postfix[i + 1] * nums[i + 1]

  

        ans = [1]*n

        for i in range(len(ans)):

            ans[i] = prefix[i]*postfix[i]

        return ans
```