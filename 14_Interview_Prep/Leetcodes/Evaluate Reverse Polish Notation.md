```python
class Solution:
    def evalRPN(self, tokens: List[str]) -> int:
        stack = []
        for tok in tokens:
            if tok in ['+', '-', '*', '/']:
                a = stack.pop()
                b = stack.pop()
                if tok == '+':
                    stack.append(b+a)
                if tok == '-':
                    stack.append(b-a)
                if tok == '*':
                    stack.append(b*a)
                if tok == '/':
                    stack.append(int(b/a))
            else:
                stack.append(int(tok))
        return stack.pop()
```
