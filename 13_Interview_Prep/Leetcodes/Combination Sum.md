```python
class Solution:
    def combinationSum(self, nums: List[int], target: int) -> List[List[int]]:
        res = []
        def backtrace(cur, vals, target):
            if target < 0:
                return
            if target == 0:
                res.append(cur)
                return
            
            for i in range(len(vals)):
                backtrace(cur + [vals[i]], vals[:i+1], target - vals[i])
        
        backtrace([], nums.copy(), target)
        return res
```
