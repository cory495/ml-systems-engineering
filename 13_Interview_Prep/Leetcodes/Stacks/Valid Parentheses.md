---
Difficulty: Easy
Topics: Stacks
---

# Valid Parentheses

This is a part of [[LeetCode Patterns]].

You are given a string `s` consisting of the following characters: `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`.

The input string `s` is valid if and only if:

1. Every open bracket is closed by the same type of close bracket.
2. Open brackets are closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.

Return `true` if `s` is a valid string, and `false` otherwise.

**Example 1:**

```java
Input: s = "[]"

Output: true
```

**Example 2:**

```java
Input: s = "([{}])"

Output: true
```

**Example 3:**

```java
Input: s = "[(])"

Output: false
```

Explanation: The brackets are not closed in the correct order.

**Constraints:**

- `1 <= s.length <= 1000`

**Solutions:**
```python
class Solution:

    def isValid(self, s: str) -> bool:

        stack = []

        for c in s:

            if c in ['(', '[', '{']:

                stack.append(c)

            else:

                if len(stack) < 1:

                    return False

                on = stack.pop()

                if (c == ')' and on != '(') or (c == ']'

                and on !='[') or (c == '}'

                and on !='{'):

                    return False

        return len(stack) == 0
```

While the bottom version is cleaner, it is not necessarily faster. This is not due a difference in computational complexity. Both are `O(n)`. Instead, this is most likely on the CPU level. Modern CPUs are greatly equipped for if-else statements. Hash maps are not as optimized on the CPU level. Thus, hash maps may take more time to run than if-else statements, even if both solutions have the same time complexity.
```python
class Solution:

    def isValid(self, s: str) -> bool:

        stack = []

        pairs = {')': '(', ']': '[', '}': '{'}

        for c in s:

            if c in pairs:

                if not stack or stack.pop() != pairs[c]:

                    return False

            else:

                stack.append(c)

        return len(stack) == 0
```