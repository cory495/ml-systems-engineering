---
Difficulty: Medium
Topics: Sliding Window
---
# Longest Substring Without Repeating Characters

This is a part of [[LeetCode Patterns]].

Given a string `s`, find the _length of the longest substring_ without duplicate characters.

A **substring** is a contiguous sequence of characters within a string.

**Example 1:**

```java
Input: s = "zxyzxyz"

Output: 3
```

Explanation: The string "xyz" is the longest without duplicate characters.

**Example 2:**

```java
Input: s = "xxxx"

Output: 1
```

**Constraints:**

- `0 <= s.length <= 1000`
- `s` may consist of printable ASCII characters.

**Solutions:**
```python
class Solution:

    def lengthOfLongestSubstring(self, s: str) -> int:

        present = set()

        max_count = 0

        left = 0

        if len(s) <= 1:

            return len(s)

        for right in range(len(s)):

            max_count = max(max_count, right-left)

            while s[right] in present:

                present.remove(s[left])

                left += 1

            present.add(s[right])

        return max(max_count, len(s)-left)
```

Small optimization to remove edge case.
```python
class Solution:

    def lengthOfLongestSubstring(self, s: str) -> int:

        present = set()

        max_count = 0

        left = 0

        if len(s) <= 1:

            return len(s)

        for right in range(len(s)):

            while s[right] in present:

                present.remove(s[left])

                left += 1

            present.add(s[right])

            max_count = max(max_count, right-left+1)

        return max_count
```