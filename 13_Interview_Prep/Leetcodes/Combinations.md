```python
class Solution:
    def combine(self, n: int, k: int) -> List[List[int]]:
        res = []
        def backtrace(cur):
            if len(cur) == k:
                res.append(cur[:])
                return
            last = cur[-1]
            for i in range(last+1, n+1):
                cur.append(i)
                backtrace(cur)
                cur.pop()

        for i in range(1, n-k+2):
            backtrace([i])
        return res
```
