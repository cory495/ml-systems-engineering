```python
class MyStack:

    def __init__(self):
        self.q = deque()

    def push(self, x: int) -> None:
        self.q.append(x)

    def pop(self) -> int:
        temp_q = deque()
        while len(self.q) > 1:
            temp_q.append(self.q.popleft())
        res = self.q.popleft()
        while temp_q:
            self.q.append(temp_q.popleft())
        return res

    def top(self) -> int:
        temp_q = deque()
        while len(self.q) > 1:
            temp_q.append(self.q.popleft())
        res = self.q[0]
        temp_q.append(self.q.popleft())
        while temp_q:
            self.q.append(temp_q.popleft())
        return res

    def empty(self) -> bool:
        return not self.q


# Your MyStack object will be instantiated and called as such:
# obj = MyStack()
# obj.push(x)
# param_2 = obj.pop()
# param_3 = obj.top()
# param_4 = obj.empty()
```

```python
class MyStack:

    def __init__(self):
        self.q = deque()

    def push(self, x: int) -> None:
        self.q.append(x)
        for _ in range(len(self.q) - 1):
            self.q.append(self.q.popleft())

    def pop(self) -> int:
        return self.q.popleft()

    def top(self) -> int:
        return self.q[0]

    def empty(self) -> bool:
        return not self.q


# Your MyStack object will be instantiated and called as such:
# obj = MyStack()
# obj.push(x)
# param_2 = obj.pop()
# param_3 = obj.top()
# param_4 = obj.empty()
```

```python
class MyStack:

    def __init__(self):
        self.q = deque()

    def push(self, x: int) -> None:
        self.q = deque([x, self.q])

    def pop(self) -> int:
        top = self.q.popleft()
        self.q = self.q.popleft()
        return top

    def top(self) -> int:
        return self.q[0]

    def empty(self) -> bool:
        return not self.q


# Your MyStack object will be instantiated and called as such:
# obj = MyStack()
# obj.push(x)
# param_2 = obj.pop()
# param_3 = obj.top()
# param_4 = obj.empty()
```
