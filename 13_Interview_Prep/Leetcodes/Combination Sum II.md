```python
class Solution:
    def combinationSum2(self, candidates: List[int], target: int) -> List[List[int]]:
        res = []
        candidates = sorted(candidates)
        def backtrace(cur, left, tar):
            if tar < 0:
                return
            if tar == 0:
                res.append(cur)
                return
            
            for i in range(left, len(candidates)):
                if i > 0 and i-1 >= left and candidates[i] == candidates[i-1]:
                    continue
                backtrace(cur + [candidates[i]], i+1, tar - candidates[i])
        
        backtrace([], 0, target)
        return res
```
