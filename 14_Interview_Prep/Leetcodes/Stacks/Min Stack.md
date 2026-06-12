---
Difficulty: Medium
Topics: Stacks
---


# Min Stack

This is a part of [[LeetCode Patterns]].

Design a stack class that supports the `push`, `pop`, `top`, and `getMin` operations.

- `MinStack()` initializes the stack object.
- `void push(int val)` pushes the element `val` onto the stack.
- `void pop()` removes the element on the top of the stack.
- `int top()` gets the top element of the stack.
- `int getMin()` retrieves the minimum element in the stack.

Each function should run in O(1)O(1) time.

**Example 1:**

```java
Input: ["MinStack", "push", 1, "push", 2, "push", 0, "getMin", "pop", "top", "getMin"]

Output: [null,null,null,null,0,null,2,1]

Explanation:
MinStack minStack = new MinStack();
minStack.push(1);
minStack.push(2);
minStack.push(0);
minStack.getMin(); // return 0
minStack.pop();
minStack.top();    // return 2
minStack.getMin(); // return 1
```

**Constraints:**

- `-2^31 <= val <= 2^31 - 1`.
- `pop`, `top` and `getMin` will always be called on **non-empty** stacks.

**Solutions:**

```python
class MinStack:

    def __init__(self):
        self.heap = []
        self.stack = []

    def push(self, val: int) -> None:
        self.stack.append(val)
        heapq.heappush(self.heap, val)

    def pop(self) -> None:
        val = self.stack.pop()
        self.heap.remove(val)
        heapq.heapify(self.heap)

    def top(self) -> int:
        return self.stack[-1]

    def getMin(self) -> int:
        return self.heap[0]
```

```python
class MinStack:
    def __init__(self):
        self.stack = []
        self.min_stack = []
    
    def push(self, val: int) -> None:
        self.stack.append(val)
        if not self.min_stack or val <= self.min_stack[-1]:
            self.min_stack.append(val)
    
    def pop(self) -> None:
        val = self.stack.pop()
        if val == self.min_stack[-1]:
            self.min_stack.pop()
    
    def top(self) -> int:
        return self.stack[-1]
    
    def getMin(self) -> int:
        return self.min_stack[-1]
```

```python
class MinStack:
    def __init__(self):
        self.stack = []
    
    def push(self, val: int) -> None:
        current_min = min(val, self.stack[-1][1] if self.stack else val)
        self.stack.append((val, current_min))
    
    def pop(self) -> None:
        self.stack.pop()
    
    def top(self) -> int:
        return self.stack[-1][0]
    
    def getMin(self) -> int:
        return self.stack[-1][1]
```

```python
class MinStack:
    def __init__(self):
        self.stack = []
        self.min_val = float('inf')
    
    def push(self, val: int) -> None:
        if val <= self.min_val:
            self.stack.append(self.min_val)
            self.min_val = val
        self.stack.append(val)
    
    def pop(self) -> None:
        val = self.stack.pop()
        if val == self.min_val:
            self.min_val = self.stack.pop()
    
    def top(self) -> int:
        return self.stack[-1]
    
    def getMin(self) -> int:
        return self.min_val
```
