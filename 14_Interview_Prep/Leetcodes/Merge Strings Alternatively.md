```python
class Solution:
    def mergeAlternately(self, word1: str, word2: str) -> str:
        n, m = len(word1), len(word2)
        i = 0
        res = ""
        while i < min(n, m):
            res += word1[i] + word2[i]
            i += 1
        res += word1[i:] + word2[i:]
        return res
```

```python
class Solution:
    def mergeAlternately(self, word1: str, word2: str) -> str:
        n, m = len(word1), len(word2)
        i = 0
        res = []
        while i < min(n, m):
            res.append(word1[i])
            res.append(word2[i])
            i += 1
        res.extend(word1[i:])
        res.extend(word2[i:])
        return ''.join(res)
```
