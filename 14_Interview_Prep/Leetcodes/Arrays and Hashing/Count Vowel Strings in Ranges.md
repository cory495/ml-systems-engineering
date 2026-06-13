---
Difficulty: Medium
Topics: Arrays
---
# Count Vowel Strings in Ranges

This is a part of [[LeetCode Patterns]].

You are given a **0-indexed** array of strings `words` and a 2D array of integers `queries`.

Each query `queries[i] = [li, ri]` asks us to find the number of strings present at the indices ranging from `li` to `ri` (both **inclusive**) of `words` that start and end with a vowel.

Return an array `ans` of size `queries.length`, where `ans[i]` is the answer to the `i-th` query.

Note that the vowel letters are `'a'`, `'e'`, `'i'`, `'o'`, and `'u'`.

**Example 1:**

```java
Input: words = ["aba","bcb","ece","aa","e"], queries = [[0,2],[1,4],[1,1]]

Output: [2,3,0]
```

Explanation: The strings starting and ending with a vowel are "aba", "ece", "aa" and "e".  
The answer to the query [0,2] is 2 (strings "aba" and "ece").  
to query [1,4] is 3 (strings "ece", "aa", "e").  
to query [1,1] is 0.  
We return [2,3,0].

**Example 2:**

```java
Input: words = ["a","e","i"], queries = [[0,2],[0,1],[2,2]]

Output: [3,2,1]
```

Explanation: Every string satisfies the conditions, so we return [3,2,1].

**Solutions:**
```python
class Solution:

    def vowelStrings(self, words: List[str], queries: List[List[int]]) -> List[int]:

        n = len(words)

        prefix = [0]*(n+1)

        vowels = ['a', 'e', 'i', 'o', 'u']

  

        def fulfill(s):

            return s[0] in vowels and s[-1] in vowels

  

        for i in range(1, n+1):

            prefix[i] = prefix[i-1] + fulfill(words[i-1])    

  

        res = []

        for q in queries:

            cur = prefix[q[1]+1] - prefix[q[0]]

            res.append(cur)

        return res
```