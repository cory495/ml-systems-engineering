```python
class Solution:

    def firstPalindrome(self, words: List[str]) -> str:

        for s in words:

            n = len(s)

            i = 0

            is_pal = True

            while i <= n // 2:

                if s[i] != s[n-i-1]:

                    is_pal = False

                    break

                i += 1

            if is_pal:

                return s

        return ""
```

```python
class Solution:
    def firstPalindrome(self, words: List[str]) -> str:
        for s in words:
            n = len(s)

            for i in range(n // 2):
                if s[i] != s[n - i - 1]:
                    break
            else:
                return s

        return ""
```

```python
class Solution:

    def firstPalindrome(self, words: List[str]) -> str:

        for s in words:

            if s == s[::-1]:

                return s

        return ""
```