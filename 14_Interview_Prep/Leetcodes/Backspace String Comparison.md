```python
class Solution(object):

    def backspaceCompare(self, S, T):

        def build(S):

            ans = []

            for c in S:

                if c != '#':

                    ans.append(c)

                elif ans:

                    ans.pop()

            return "".join(ans)

        return build(S) == build(T)
```

```python
class Solution:

    def backspaceCompare(self, s: str, t: str) -> bool:

        i, j = len(s) - 1, len(t) - 1

  

        while i >= 0 or j >= 0:

            # Find next valid character in s

            skip = 0

            while i >= 0:

                if s[i] == '#':

                    skip += 1

                elif skip:

                    skip -= 1

                else:

                    break

                i -= 1

  

            # Find next valid character in t

            skip = 0

            while j >= 0:

                if t[j] == '#':

                    skip += 1

                elif skip:

                    skip -= 1

                else:

                    break

                j -= 1

  

            # Compare characters

            if i >= 0 and j >= 0:

                if s[i] != t[j]:

                    return False

            elif i >= 0 or j >= 0:

                return False

  

            i -= 1

            j -= 1

  

        return True
```