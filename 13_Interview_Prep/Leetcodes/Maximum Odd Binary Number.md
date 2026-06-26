```python
class Solution:
    def maximumOddBinaryNumber(self, s: str) -> str:
        counts = Counter(s)
        res = []

        res.extend(['1']*(counts['1']-1))
        res.extend(['0']*counts['0'])
        res.append('1')
        return "".join(res)
```
