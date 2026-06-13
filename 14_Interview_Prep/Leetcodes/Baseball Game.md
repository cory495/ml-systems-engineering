```python
class Solution:

    def calPoints(self, operations: List[str]) -> int:

        stack = []

        for oper in operations:

            if oper in ['+', 'D', 'C']:

                a = stack[-1]

                if oper == '+':

                    b = stack[-2]

                    stack.append(a+b)

                if oper == 'D':

                    stack.append(2*a)

                if oper == 'C':

                    stack.pop()

            else:

                stack.append(int(oper))

        return sum(stack)
```

```python
class Solution:

    def calPoints(self, operations: List[str]) -> int:

        stack = []

        push = stack.append

        pop = stack.pop

  

        for op in operations:

            if op == '+':

                push(stack[-1] + stack[-2])

            elif op == 'D':

                push(2 * stack[-1])

            elif op == 'C':

                pop()

            else:

                push(int(op))

  

        return sum(stack)
```