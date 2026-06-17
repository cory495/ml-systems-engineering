```python
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        res = []

        for num in nums:
            r = len(res)
            for i in range(r):
                res.append([num] + res[i])
            res.append([num])
        res.append([])
        return res
```
