```python
class Solution:
    def minimumTotal(self, triangle: List[List[int]]) -> int:
        height = len(triangle)
        for lvl in range(1, height):
            for idx in range(lvl + 1):
                min_val = float('inf')
                if idx-1 >= 0:
                    min_val = min(triangle[lvl-1][idx-1], min_val)
                if idx < len(triangle[lvl-1]):
                    min_val = min(triangle[lvl-1][idx], min_val)
                triangle[lvl][idx] += min_val
        return min(triangle[-1])
```
