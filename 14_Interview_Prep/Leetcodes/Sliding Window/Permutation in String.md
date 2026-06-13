---
Difficulty: Medium
Topics: Sliding Window
---
# Permutation in String

This is a part of [[LeetCode Patterns]].

You are given two strings `s1` and `s2`.

Return `true` if `s2` contains a permutation of `s1`, or `false` otherwise. That means if a permutation of `s1` exists as a substring of `s2`, then return `true`.

Both strings only contain lowercase letters.

**Example 1:**

```java
Input: s1 = "abc", s2 = "lecabee"

Output: true
```

Explanation: The substring `"cab"` is a permutation of `"abc"` and is present in `"lecabee"`.

**Example 2:**

```java
Input: s1 = "abc", s2 = "lecaabee"

Output: false
```

**Constraints:**

- `1 <= s1.length, s2.length <= 1000`

**Solutions:**

```python
class Solution:
    def checkInclusion(self, s1: str, s2: str) -> bool:
        if len(s1) > len(s2):
            return False
            
        chars = [0] * 26
        
        def getIndex(c):
            return ord(c) - ord('a')
        
        # Count characters in s1
        for c in s1:
            chars[getIndex(c)] += 1
        
        left = 0
        for right in range(len(s2)):
            # Add current character
            chars[getIndex(s2[right])] -= 1
            
            # If window is too big, remove leftmost character
            if right - left + 1 > len(s1):
                chars[getIndex(s2[left])] += 1
                left += 1
            
            # Check if current window is a permutation
            if right - left + 1 == len(s1) and all(count == 0 for count in chars):
                return True
        
        return False
```
