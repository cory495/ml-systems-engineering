---
Difficulty: Medium
Topics: Greedy
Created: 2026-06-28
Updated: 2026-06-28
tags:
  - interview
  - programming
  - greedy
Type: Interview
---

# Partition Labels

You are given a string `s` consisting of lowercase english letters.

We want to split the string into as many substrings as possible, while ensuring that each letter appears in at most one substring.

Return a list of integers representing the size of these substrings in the order they appear in the string.

**Example 1:**

```java
Input: s = "xyxxyzbzbbisl"

Output: [5, 5, 1, 1, 1]
```

Explanation: The string can be split into `["xyxxy", "zbzbb", "i", "s", "l"]`.

**Example 2:**

```java
Input: s = "abcabc"

Output: [6]
```

**Constraints:**

- `1 <= s.length <= 100`

**Solutions:

```python
class Solution:

    def partitionLabels(self, s: str) -> List[int]:

        count = Counter(s)

        ins = [-1] * 26

        res = []

  

        i = 0

        for c in s:

            idx = ord(c) - ord('a')

            i += 1

            if ins[idx] == -1:

                ins[idx] = count[c]

            ins[idx] -= 1

            if ins[idx] == 0:

                ins[idx] = -1

                if sum(ins) == -26:

                    res.append(i)

                    i = 0

        return res
```

```python
class Solution:

    def partitionLabels(self, s: str) -> List[int]:

        last = {c: i for i, c in enumerate(s)}

  

        res = []

        start = end = 0

  

        for i, c in enumerate(s):

            end = max(end, last[c])

  

            if i == end:

                res.append(end - start + 1)

                start = i + 1

  

        return res
```