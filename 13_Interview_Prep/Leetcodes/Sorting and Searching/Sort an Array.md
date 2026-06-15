---
Difficulty: Medium
Topics: Sorting
---
# Sort an Array

This is a part of [[LeetCode Patterns]].

You are given an array of integers `nums`, sort the array in ascending order and return it.

You must solve the problem **without using any built-in functions** in `O(nlog(n))` time complexity and with the smallest space complexity possible.

**Example 1:**

```java
Input: nums = [10,9,1,1,1,2,3,1]

Output: [1,1,1,1,2,3,9,10]
```

**Example 2:**

```java
Input: nums = [5,10,2,1,3]

Output: [1,2,3,5,10]
```

**Constraints:**

- `1 <= nums.length <= 50,000`.
- `-50,000 <= nums[i] <= 50,000`

**Solutions:**

```python
class Solution:
    def sortArray(self, nums: List[int]) -> List[int]:
        def merge_sort(nums):
            n = len(nums)
            if n < 2:
                return nums
            mid = n // 2
            return merge(merge_sort(nums[:mid]), merge_sort(nums[mid:]))

        def merge(nums1, nums2):
            i, j = 0, 0
            n, m = len(nums1), len(nums2)
            ans = []

            while i < n and j < m:
                if nums1[i] < nums2[j]:
                    ans = ans + [nums1[i]]
                    i += 1
                else:
                    ans = ans + [nums2[j]]
                    j += 1
            if i < n:
                ans = ans + nums1[i:]
            if j < m:
                ans = ans + nums2[j:]
            return ans
        
        return merge_sort(nums)
```
```python
```python
class Solution:
    def sortArray(self, nums: List[int]) -> List[int]:
        def merge_sort(nums):
            if len(nums) <= 1:
                return nums
            
            mid = len(nums) // 2
            left = merge_sort(nums[:mid])
            right = merge_sort(nums[mid:])
            return merge(left, right)

        def merge(nums1, nums2):
            i = j = 0
            result = []
            
            while i < len(nums1) and j < len(nums2):
                if nums1[i] <= nums2[j]:
                    result.append(nums1[i])
                    i += 1
                else:
                    result.append(nums2[j])
                    j += 1
            
            result.extend(nums1[i:])
            result.extend(nums2[j:])
            return result
        
        return merge_sort(nums)
```
