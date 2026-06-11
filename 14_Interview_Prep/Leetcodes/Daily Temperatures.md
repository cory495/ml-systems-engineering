```python
class Solution:
    def dailyTemperatures(self, temperatures: List[int]) -> List[int]:
        n = len(temperatures)
        stack = [0]
        result = [0]*n

        for i in range(1,n):
            if temperatures[i] > temperatures[i-1]:
                while len(stack) > 0 and temperatures[stack[-1]] < temperatures[i]:
                    idx = stack.pop()
                    result[idx] = i - idx
            stack.append(i)
        return result
```
