```python
class Solution:
    def isMonotonic(self, nums: List[int]) -> bool:
        n = len(nums)
        for i in range(1, n):
            if nums[i] > nums[i-1]:
                break
        else:
            return True

        for i in range(1, n):
            if nums[i] < nums[i-1]:
                break
        else:
            return True
        return False
```

```python
class Solution:
    def isMonotonic(self, nums: List[int]) -> bool:
        increase = decrease = True

        for i in range(len(nums) - 1):
            if not nums[i] <= nums[i+1]:
                increase = False
            if not nums[i] >= nums[i+1]:
                decrease = False
        return increase or decrease
```
