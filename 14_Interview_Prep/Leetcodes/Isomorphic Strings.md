**Solutions:**

```python
class Solution:

    def isIsomorphic(self, s: str, t: str) -> bool:

        dt = {}

        n, m = len(s), len(t)

        if n != m:

            return False

  

        for i in range(n):

            if dt.get(s[i], -1) == -1 and t[i] not in dt.values():

                dt[s[i]] = t[i]

            elif t[i] in dt.values() and s[i] not in dt:

                return False

            elif dt[s[i]] != t[i]:

                return False

        return True
```

```python
class Solution:

    def isIsomorphic(self, s: str, t: str) -> bool:

        if len(s) != len(t):

            return False

  

        s_to_t = {}

        t_to_s = {}

  

        for a, b in zip(s, t):

            if a in s_to_t and s_to_t[a] != b:

                return False

            if b in t_to_s and t_to_s[b] != a:

                return False

  

            s_to_t[a] = b

            t_to_s[b] = a

  

        return True
```