---
Difficulty: Medium
Topics: Heaps
---

# Kth Largest Element in Array

This is a part of [[LeetCode Patterns]].

Given an unsorted array of integers `nums` and an integer `k`, return the `kth` largest element in the array.

By `kth` largest element, we mean the `kth` largest element in the sorted order, not the `kth` distinct element.

Follow-up: Can you solve it without sorting?

**Example 1:**

```java
Input: nums = [2,3,1,5,4], k = 2

Output: 4
```

**Example 2:**

```java
Input: nums = [2,3,1,1,5,5,4], k = 3

Output: 4
```

**Constraints:**

- `1 <= k <= nums.length <= 10000`
- `-1000 <= nums[i] <= 1000`

**Solutions:**

```python
class Solution:

    def findKthLargest(self, nums: List[int], k: int) -> int:

        heapq.heapify(nums)

        return heapq.nlargest(k, nums)[-1]
```

```python
class Solution:

    def findKthLargest(self, nums: List[int], k: int) -> int:

        heapq.heapify(nums)

        return heapq.nlargest(k, nums)[-1]
```

```python
class Solution:

    def findKthLargest(self, nums, k):

        k = len(nums) - k

        l, r = 0, len(nums) - 1

  

        while True:

            pivot = nums[r]

            p = l

  

            for i in range(l, r):

                if nums[i] <= pivot:

                    nums[i], nums[p] = nums[p], nums[i]

                    p += 1

  

            nums[p], nums[r] = nums[r], nums[p]

  

            if p < k:

                l = p + 1

            elif p > k:

                r = p - 1

            else:

                return nums[p]
```