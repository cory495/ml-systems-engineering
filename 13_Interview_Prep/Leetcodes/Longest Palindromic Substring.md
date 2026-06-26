---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - interview
  - programming
Type: Interview
---
```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        l = r = 0
        max_str = ""
        n = len(s)

        while r < n:
            while s[l:r+1] != s[l:r+1][::-1]:
                l += 1
            if r-l+1 > len(max_str):
                max_str = s[l:r+1]
            r += 1
            l = 0
        return max_str
```
