---
Difficulty: Easy
Topics: Two Pointers
---

# Valid Palindrome

This is a part of [[LeetCode Patterns]].

Given a string `s`, return `true` if it is a **palindrome**, otherwise return `false`.

A **palindrome** is a string that reads the same forward and backward. It is also case-insensitive and ignores all non-alphanumeric characters.

**Note:** Alphanumeric characters consist of letters `(A-Z, a-z)` and numbers `(0-9)`.

**Example 1:**

```java
Input: s = "Was it a car or a cat I saw?"

Output: true
```

Explanation: After considering only alphanumerical characters we have "wasitacaroracatisaw", which is a palindrome.

**Example 2:**

```java
Input: s = "tab a cat"

Output: false
```

Explanation: "tabacat" is not a palindrome.

**Constraints:**

- `1 <= s.length <= 1000`
- `s` is made up of only printable ASCII characters.

**Solutions:**
```python
class Solution:

    def isPalindrome(self, s: str) -> bool:

        s = re.sub(r'[^a-zA-Z0-9]', '', s).lower()

        for i in range(len(s) // 2):

            if s[i] != s[len(s)-i-1]:

                return False

        return True
```

The bottom does not use a regular expression, thus it is faster for larger strings.
```python
class Solution:

    def isPalindrome(self, s: str) -> bool:

        l, r = 0, len(s)-1

        while l < r:

            while l < r and  not s[l].isalnum():

                l += 1

            while l < r and  not s[r].isalnum():

                r -= 1

            if s[l].lower() != s[r].lower():

                return False

            l += 1

            r -= 1

        return True
```

Doing the is alphanumerical check once speeds up the algorithm.
```python
class Solution:

    def isPalindrome(self, s: str) -> bool:

        isalnum = str.isalnum

        lower = str.lower

        l, r = 0, len(s) - 1

  

        while l < r:

            while l < r and not isalnum(s[l]):

                l += 1

            while l < r and not isalnum(s[r]):

                r -= 1

            if lower(s[l]) != lower(s[r]):

                return False

            l += 1

            r -= 1

  

        return True
```