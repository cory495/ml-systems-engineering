---
Difficulty: Medium
Topics: Stacks
---
# Evaluate Reverse Polish Notation

You are given an array of strings `tokens` that represents a **valid** arithmetic expression in [Reverse Polish Notation](https://en.wikipedia.org/wiki/Reverse_Polish_notation).

Return the integer that represents the evaluation of the expression.

- The operands may be integers or the results of other operations.
- The operators include `'+'`, `'-'`, `'*'`, and `'/'`.
- Assume that division between integers always truncates toward zero.

**Example 1:**

```java
Input: tokens = ["1","2","+","3","*","4","-"]

Output: 5

Explanation: ((1 + 2) * 3) - 4 = 5
```

**Constraints:**

- `1 <= tokens.length <= 1000`.
- tokens[i] is `"+"`, `"-"`, `"*"`, or `"/"`, or a string representing an integer in the range `[-200, 200]`.

**Solutions:**

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
