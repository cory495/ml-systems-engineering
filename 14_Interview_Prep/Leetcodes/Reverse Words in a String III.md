**Solutions:**

```python
class Solution:

    def reverseWords(self, s: str) -> str:

        s = s.split(' ')

        for i in range(len(s)):

            s[i] = s[i][::-1]

        return ' '.join(s)
```

```python
class Solution:
    def reverseWords(self, s: str) -> str:
        return ' '.join(word[::-1] for word in s.split(' '))
```