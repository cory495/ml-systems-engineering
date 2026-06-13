```python
class Solution:

    def findContentChildren(self, g: List[int], s: List[int]) -> int:

        g.sort()

        s.sort()

        n, m = len(g), len(s)

        i, j = 0, 0

        res = 0

  

        while i < n and j < m:

            if s[j] >= g[i]:

                res += 1

                i += 1

            j += 1

        return res
```