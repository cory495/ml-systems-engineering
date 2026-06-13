**Solutions:**

```python
class Solution:
    def containsNearbyDuplicate(self, nums: List[int], k: int) -> bool:
        left = right = 0
        vals = set()
        while right < len(nums):
            if len(vals) > k:
                vals.remove(nums[left])
                left += 1
            if nums[right] in vals:
                return True
            vals.add(nums[right])
            right += 1
        return False
```
