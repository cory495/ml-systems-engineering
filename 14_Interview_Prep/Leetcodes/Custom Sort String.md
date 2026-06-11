```python
class Solution:
    def customSortString(self, order: str, s: str) -> str:
        dt = {}
        for c in order:
            dt[c] = 0
        
        for c in s:
            if dt.get(c, -1) != -1:
                dt[c] += 1
        
        ans = ""

        for c in order:
            ans += c*dt[c]
        
        for c in s:
            if dt.get(c, -1) == -1:
                ans += c
        
        return ans
```
