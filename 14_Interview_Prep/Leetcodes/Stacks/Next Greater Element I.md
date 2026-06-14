---
Difficulty: Easy
Topics: Stacks
---
# Next Greater Element I

This is a part of [[LeetCode Patterns]].

The **next greater element** of some element `x` in an array is the **first greater element** that is to the right of `x` in the array.

You are given two **0-indexed** integer arrays `nums1` and `nums2`, where `nums1` is a subset of `nums2`. `nums2` contains **unique** elements.

For each `0 <= i < nums1.length`, find the index `j` such that `nums1[i] == nums2[j]` and determine the **next greater element** of `nums2[j]` in `nums2`. If there is no next greater element, then the answer for this query is `-1`.

**Example 1:**

```java
Input: nums1 = [4,1,2], nums2 = [1,3,4,2]

Output: [-1,3,-1]
```

Explanation:

- There is no next greater element for `4`.
- `3` is the next greater element for `1`.
- There is no next greater element for `2`.

**Example 2:**

```java
Input: nums1 = [2,4], nums2 = [1,2,3,4]

Output: [3,-1]
```

Explanation:

- `3` is the next greater element for `2`.
- There is no next greater element for `4`.

**Constraints:**

- `1 <= nums1.length <= nums2.length <= 1000`
- `0 <= nums1[i], nums2[i] <= 10,000`
- All integers in `nums1` and `nums2` are **unique**.
- All the integers of `nums1` also appear in `nums2`.

**Follow up:** Could you find an `O(nums1.length + nums2.length)` solution?


**Solutions:**

```python
class Solution:

    def nextGreaterElement(self, nums1: List[int], nums2: List[int]) -> List[int]:

        dt = {}

        stack = []

  

        for num in nums2:

            while stack and stack[-1] < num:

                dt[stack.pop()] = num

  

            stack.append(num)

  

        return [dt.get(num, -1) for num in nums1]
```