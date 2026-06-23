```python
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        res = []

        def backtrack(to_add, open_ct, closed_ct):
            if len(to_add) == 2 * n:
                res.append(to_add)
                return
            if open_ct < n:
                backtrack(to_add + '(', open_ct + 1, closed_ct)
            if closed_ct < open_ct:
                backtrack(to_add + ')', open_ct, closed_ct + 1)
        backtrack("", 0, 0)
        return res
```
