---
Difficulty: Hard
Topics: Sliding Window
---
# Sliding Window Maximum

You are given an array of integers `nums` and an integer `k`. There is a sliding window of size `k` that starts at the left edge of the array. The window slides one position to the right until it reaches the right edge of the array.

Return a list that contains the maximum element in the window at each step.

**Example 1:**

```java
Input: nums = [1,2,1,0,4,2,6], k = 3

Output: [2,2,4,4,6]

Explanation:
Window position            Max
---------------           -----
[1  2  1] 0  4  2  6        2
 1 [2  1  0] 4  2  6        2
 1  2 [1  0  4] 2  6        4
 1  2  1 [0  4  2] 6        4
 1  2  1  0 [4  2  6]       6
```

**Constraints:**

- `1 <= nums.length <= 100,000`
- `-10,000 <= nums[i] <= 10,000`
- `1 <= k <= nums.length`

**Solutions:**

```python
class Solution:

    def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:

        heap = []

        res = []

        for i in range(len(nums)):

            heapq.heappush_max(heap, nums[i])

            if len(heap) > k:

                heap.remove(nums[i-k])

                heapq.heapify_max(heap)

            if len(heap) == k:

                res.append(heap[0])

        return res
```

```python
class Solution:

    def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:

        dq = deque()

        res = []

  

        for i in range(len(nums)):

  

            while dq and dq[0] <= i - k:

                dq.popleft()

  

            while dq and nums[dq[-1]] <= nums[i]:

                dq.pop()

  

            dq.append(i)

  

            if i >= k - 1:

                res.append(nums[dq[0]])

  

        return res
```