```python
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        res = []
        n = len(nums)
        
        def backtrace(i, subset):
            if i == n:
                res.append(subset)
                return
            for j in range(i, n):
                new_subset = subset[::]
                new_subset[i], new_subset[j] = new_subset[j], new_subset[i]
                backtrace(i+1, new_subset)
        
        backtrace(0, nums)
        return res
```

```python
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        res = []
        n = len(nums)
        
        def backtrace(i):
            if i == n:
                res.append(nums[::])
                return
            for j in range(i, n):
                nums[i], nums[j] = nums[j], nums[i]
                backtrace(i+1)
                nums[i], nums[j] = nums[j], nums[i]
        
        backtrace(0)
        return res
```
