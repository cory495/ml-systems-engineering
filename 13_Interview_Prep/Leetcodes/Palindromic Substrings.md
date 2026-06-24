```python
class Solution:
    def countSubstrings(self, s: str) -> int:
        l = r = 0
        ct = 0
        n = len(s)

        while r < n:
            while l <= r:
                if s[l:r+1] == s[l:r+1][::-1]:
                    ct += 1
                l += 1
            r += 1
            l = 0
        return ct
```
