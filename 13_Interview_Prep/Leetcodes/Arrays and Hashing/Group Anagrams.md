---
Difficulty: Medium
Topics: Arrays
---
# Group Anagrams

This is a part of [[LeetCode Patterns]].

Given an array of strings `strs`, group all _anagrams_ together into sublists. You may return the output in **any order**.

An **anagram** is a string that contains the exact same characters as another string, but the order of the characters can be different.

**Example 1:**

```java
Input: strs = ["act","pots","tops","cat","stop","hat"]

Output: [["hat"],["act", "cat"],["stop", "pots", "tops"]]
```

**Example 2:**

```java
Input: strs = ["x"]

Output: [["x"]]
```

**Example 3:**

```java
Input: strs = [""]

Output: [[""]]
```

**Constraints:**

- `1 <= strs.length <= 1000`.
- `0 <= strs[i].length <= 100`
- `strs[i]` is made up of lowercase English letters.

```python
class Solution:

    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:

        dt = {}

        for s in strs:

            key = str(sorted(s))

            dt[key] = dt.get(key, []) + [s]

        return list(dt.values())
```

The initial solution uses sorting. Sorting causes this solution to be `O(nklogk)` where `k` is the average string length and `n` is the number of strings. To overcome this, `ord(c)` is used. This way, the solution becomes `O(nk)`. I considered using a dictionary instead of `ord(c)`; however, `ord(c)` is the more optimal solution.
```python
class Solution:

    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:

        ans = {}

        for s in strs:

            count = [0] * 26

            for c in s:

                count[ord(c) - ord('a')] += 1

            key = tuple(count)

            ans[key] = ans.get(key, []) + [s]

        return list(ans.values())
```