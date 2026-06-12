---
Difficulty: Easy
Topics: Two Pointers
---

# Valid Palindrome II

You are given a string `s`, return true if the `s` can be a palindrome after deleting at most one character from it.

A **palindrome** is a string that reads the same forward and backward.

**Note:** Alphanumeric characters consist of letters `(A-Z, a-z)` and numbers `(0-9)`.

**Example 1:**

```java
Input: s = "aca"

Output: true
```

Explanation: "aca" is already a palindrome.

**Example 2:**

```java
Input: s = "abbadc"

Output: false
```

Explanation: "abbadc" is not a palindrome and can't be made a palindrome after deleting at most one character.

**Example 3:**

```java
Input: s = "abbda"

Output: true
```

Explanation: "We can delete the character 'd'.

**Constraints:**

- `1 <= s.length <= 100,000`
- `s` is made up of only lowercase English letters.

```python
class Solution:

    def validPalindrome(self, s: str) -> bool:

        def is_palindrome(left, right):

            while left < right:

                if s[left] != s[right]:

                    return False

                left += 1

                right -= 1

            return True

        left, right = 0, len(s)-1

        hasDeleted = False

        while left < right:

            if s[left] != s[right]:

                return (

                    is_palindrome(left + 1, right) or

                    is_palindrome(left, right - 1)

                )

            else:

                left += 1

                right -= 1

        return True
```