```python
class Solution:

    def addSpaces(self, s: str, spaces: List[int]) -> str:

        i = j = 0

        n, m = len(s), len(spaces)

        res = []

  

        while i < n:

            if j < m and i == spaces[j]:

                res.append(' ')

                j += 1

            res.append(s[i])

            i += 1

        return ''.join(res)
```

```python
class Solution:

    def addSpaces(self, s: str, spaces: List[int]) -> str:

        res = []

        prev = 0

  

        for pos in spaces:

            res.append(s[prev:pos])

            prev = pos

  

        res.append(s[prev:])

        return ' '.join(res)
```