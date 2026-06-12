# Stacks

## Core Idea
A stack is a LIFO (Last In, First Out) data structure used for nested structure, matching problems, and backtracking.

---

## Operations
```python
stack.append(x)
stack.pop()
```

---

## When to Use Stacks
- Matching parentheses
- Nested structure problems
- "most recent" element processing
- monotonic ordering problems

---

## Valid Parentheses Pattern
Use stack to match opening and closing brackets.

---

## Monotonic Stack

Used for:
- Next Greater Element
- Daily Temperatures
- Histogram problems

```python
stack = []

for i in range(len(nums)):
    while stack and nums[i] > nums[stack[-1]]:
        stack.pop()
    stack.append(i)
```

---

## Key Insight
Stack keeps track of previous unresolved elements.

---

## Complexity
Push: O(1)
Pop: O(1)
Total: O(n)

---
## Relevant Problems
### Easy
- down:: [[Valid Parentheses]]
### Medium
- down:: [[Daily Temperatures]]
- down:: [[Evaluate Reverse Polish Notation]]
- down:: [[Min Stack]]