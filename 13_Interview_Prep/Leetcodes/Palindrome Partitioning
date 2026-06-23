```python
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        res = []
        n = len(s)
        def backtrack(left, to_add):
            if left == n:
                res.append(to_add[:])
                return
            for i in range(left+1, n+1):
                if s[left:i] == s[left:i][::-1]:
                    to_add.append(s[left:i])
                    backtrack(i, to_add)
                    to_add.pop()
        
        backtrack(0, [])
        return res
```
