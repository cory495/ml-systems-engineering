

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