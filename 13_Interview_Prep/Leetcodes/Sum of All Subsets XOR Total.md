```python
class Solution:
    def subsetXORSum(self, nums: List[int]) -> int:
        res = 0

        def dfs(i, xored):
            nonlocal res
            if i >= len(nums):
                res += xored
                return
            dfs(i+1, xored^nums[i])
            dfs(i+1, xored)

        dfs(0, 0)
        return res
```

```python
class Solution:
    def subsetXORSum(self, nums: List[int]) -> int:
        res = 0
        for num in nums:
            res |= num
        return res << (len(nums) - 1)
```
