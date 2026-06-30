```python
class Solution:
    def tribonacci(self, n: int) -> int:
        t0, t1, t2 = 0, 1, 1
        if n == 0:
            return t0
        if n == 1:
            return t1
        for i in range(n-2):
            t0, t1, t2 = t1, t2, t0+t1+t2
        return t2
```

```python
class Solution:
    def tribonacci(self, n: int) -> int:
        t = [0, 1, 1]
        if n < 3:
            return t[n]
        for i in range(n-2):
            t[i % 3] = sum(t)
        return t[n % 3]
```
