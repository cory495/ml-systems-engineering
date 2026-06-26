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

```python
class Solution:
    def maximumOddBinaryNumber(self, s: str) -> str:
        count = 0
        for c in s:
            if c == "1":
                count += 1

        return (count - 1) * "1" + (len(s) - count) * "0" + "1"
```
