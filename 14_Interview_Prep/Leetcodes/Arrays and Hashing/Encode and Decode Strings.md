---
Difficulty: Medium
Topics: Arrays
---

# Encode and Decode Strings

This is a part of [[LeetCode Patterns]].
Design an algorithm to encode **a list of strings** to **a string**. The **encoded string** is then sent over the network and is **decoded** back to the **original list** of strings.

**Machine 1 (sender)** has the function:

```java
String encode(List<String> strs) {
    // ... your code
    return encoded_string;
}
```

**Machine 2 (receiver)** has the function:

```java
List<String> decode(String encoded_string) {
    // ... your code
    return decoded_strs;
}
```

So **Machine 1** does:

```java
String encoded_string = encode(strs);
```

and **Machine 2** does:

```java
List<String> decoded_strs = decode(encoded_string);
```

`decoded_strs` in Machine 2 should be the **same** as the input `strs` in Machine 1.

Implement the `encode` and `decode` methods.

**Example 1:**

```java
Input: strs = ["Hello","World"]

Output: ["Hello","World"]
```

**Explanation:**

```java
Solution solution = new Solution();
String encoded_string = solution.encode(strs);

// Machine 1 ---encoded_string---> Machine 2

List<String> decoded_strs = solution.decode(encoded_string);
```

  

**Example 2:**

```java
Input: strs = [""]

Output: [""]
```

  

**Constraints:**

- `0 <= strs.length < 100`
- `0 <= strs[i].length < 200`
- `strs[i]` contains any possible characters out of `256` valid ASCII characters.

  

**Follow up:** Could you write a generalized algorithm to work on any possible set of characters?

**Solutions:**
```python
class Solution:

    def encode(self, strs: List[str]) -> str:

        if not strs:

            return 'ñ'

        return 'é'.join(strs)

    def decode(self, s: str) -> List[str]:

        if s == 'ñ':

            return []

        if not s:

            return [""]

        return s.split('é')
```

The above is the naive solution of using a random non-ASCII value. The thought of not needing to use non-ASCII values is important. I, then, thought to use the length but what if the string contained numbers at the beginning. Thus, `'#'` was used to separated the length from the string.
```python
class Solution:

    def encode(self, strs: List[str]) -> str:

        res = []

        for s in strs:

            res.append(f"{len(s)}#{s}")

        return "".join(res)

    def decode(self, s: str) -> List[str]:

        res = []

        i = 0

        while i < len(s):

            j = i

            while s[j] != "#":

                j += 1

            length = int(s[i:j])

            j += 1

            # read string of that length

            res.append(s[j:j+length])

            i = j + length

        return res
```