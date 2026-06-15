---
Difficulty: Easy
Topics: Math
---
# Plus One

This is a part of [[LeetCode Patterns]].

You are given an integer array `digits`, where each `digits[i]` is the `ith` digit of a large integer. It is ordered from most significant to least significant digit, and it will not contain any leading zero.

Return the digits of the given integer after incrementing it by one.

**Example 1:**

```java
Input: digits = [1,2,3,4]

Output: [1,2,3,5]
```

Explanation `1234` + `1` = `1235`.

**Example 2:**

```java
Input: digits = [9,9,9]

Output: [1,0,0,0]
```

**Constraints:**

- `1 <= digits.length <= 100`
- `0 <= digits[i] <= 9`

**Solutions:**

```python
class Solution:

    def plusOne(self, digits: List[int]) -> List[int]:

        carry = 1

        for i in reversed(range(len(digits))):

            val = digits[i] + carry

            if val >= 10: carry = 1

            else: carry = 0

            val %= 10

            digits[i] = val

        if carry == 1:

            return [1] + digits

        else:

            return digits
```

```python
class Solution:

    def plusOne(self, digits: List[int]) -> List[int]:

        carry = 1

        for i in reversed(range(len(digits))):

            val = digits[i] + carry

            digits[i] = val % 10

  

            if val >= 10: carry = 1

            else: return digits

        return [1] + digits
        
```