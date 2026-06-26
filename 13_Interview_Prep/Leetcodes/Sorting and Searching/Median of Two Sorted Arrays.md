---
Difficulty: Hard
Topics: Sorting
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - interview
  - programming
Type: Interview
---
# Median of Two Sorted Arrays

This is a part of [[LeetCode Patterns]].

You are given two integer arrays `nums1` and `nums2` of size `m` and `n` respectively, where each is sorted in ascending order. Return the [median](https://en.wikipedia.org/wiki/Median) value among all elements of the two arrays.

Your solution must run in O(log(m+n))O(log(m+n)) time.

**Example 1:**

```java
Input: nums1 = [1,2], nums2 = [3]

Output: 2.0
```

Explanation: Among `[1, 2, 3]` the median is 2.

**Example 2:**

```java
Input: nums1 = [1,3], nums2 = [2,4]

Output: 2.5
```

Explanation: Among `[1, 2, 3, 4]` the median is (2 + 3) / 2 = 2.5.

**Constraints:**

- `nums1.length == m`
- `nums2.length == n`
- `0 <= m <= 1000`
- `0 <= n <= 1000`
- `-10^6 <= nums1[i], nums2[i] <= 10^6`

**Solutions:**

```python
class Solution:

    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:

        if len(nums2) < len(nums1):

            nums1, nums2 = nums2, nums1

        len1, len2 = len(nums1), len(nums2)

        total = len1 + len2

        half = total // 2

        l, r = 0, len1-1

  

        while True:

            mid1 = (l + r) // 2

            mid2 = half - mid1 - 2

  

            left1 = nums1[mid1] if mid1 >= 0 else float('-inf')

            right1 = nums1[mid1 + 1] if mid1+1 < len1 else float('inf')

            left2 = nums2[mid2] if mid2 >= 0 else float('-inf')

            right2 = nums2[mid2 + 1] if mid2+1 < len2 else float('inf')

  

            if left1 <= right2 and left2 <= right1:

                if total % 2:

                    return min(right1, right2)

                return (max(left1, left2) + min(right1, right2)) / 2

            elif left1 > right2:

                r = mid1 - 1

            else:

                l = mid1 + 1
```