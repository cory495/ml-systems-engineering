---
Difficulty: Medium
Topics: Arrays
---

# Top K Frequent Elements

This is a part of [[LeetCode Patterns]].

Given an integer array `nums` and an integer `k`, return the `k` most frequent elements within the array.

The test cases are generated such that the answer is always **unique**.

You may return the output in **any order**.

**Example 1:**

```java
Input: nums = [1,2,2,3,3,3], k = 2

Output: [2,3]
```

**Example 2:**

```java
Input: nums = [7,7], k = 1

Output: [7]
```

**Constraints:**

- `1 <= nums.length <= 10^4`.
- `-1000 <= nums[i] <= 1000`
- `1 <= k <= number of distinct elements in nums`.

**Solutions:**

```python
class Solution:

    def topKFrequent(self, nums: List[int], k: int) -> List[int]:

        freq = {}

        for n in nums:

            freq[n] = freq.get(n, 0) + 1

        ans = []

        for i in range(k):

            key = max(freq, key=freq.get)

            ans.append(key)

            freq[key] = -1

        return ans
```

The first method was to simply get the key from the max of the values in the hash map `freq`. However, this has a worst case of $O(n^2)$. While brainstorming different ways to improve this, the main idea that came to mind was creating an array of arrays or a dictionary of arrays. The array of arrays won out because it can be faster and can be sorted while created. This leads to the following solution of `O(n log k)`: 
```python
class Solution:

    def topKFrequent(self, nums: List[int], k: int) -> List[int]:

        freq = {}

        for n in nums:

            freq[n] = freq.get(n, 0) + 1

        bucket = [[] for _ in range(len(nums) + 1)]

        for num, count in freq.items():

            bucket[count].append(num)

        ans = []

        for i in range(len(bucket) - 1, 0, -1):

            for num in bucket[i]:

                ans.append(num)

                if len(ans) == k:

                    return ans
```