```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        dt = {
            '2': ['a', 'b', 'c'],
            '3': ['d', 'e', 'f'],
            '4': ['g', 'h', 'i'],
            '5': ['j', 'k', 'l'],
            '6': ['m', 'n', 'o'],
            '7': ['p', 'q', 'r', 's'],
            '8': ['t', 'u', 'v'],
            '9': ['w', 'x', 'y', 'z']
        }
        if len(digits) < 1:
            return []
        res = dt[digits[0]]

        for c in digits[1:]:
            replace = []
            for char in dt[c]:
                for i in range(len(res)):
                    replace.append(res[i] + char)
            res = replace
        return res
```

```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        dt = {
            '2': ['a', 'b', 'c'],
            '3': ['d', 'e', 'f'],
            '4': ['g', 'h', 'i'],
            '5': ['j', 'k', 'l'],
            '6': ['m', 'n', 'o'],
            '7': ['p', 'q', 'r', 's'],
            '8': ['t', 'u', 'v'],
            '9': ['w', 'x', 'y', 'z']
        }
        if len(digits) == 0:
            return []
        res = []

        def backtrace(i=0, cur=""):
            if len(digits) == len(cur):
                res.append(cur)
                return
            
            for c in dt[digits[i]]:
                backtrace(i+1, cur+c)
        
        backtrace()
        return res
```
