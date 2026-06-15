---
Difficulty: Easy
Topics: Arrays
---
# Unique Email Addresses

This is a part of [[LeetCode Patterns]].

A **valid email** consists of a **local name** and a **domain name**, separated by the `'@'` sign. Besides lowercase letters, the email may contain one or more `'.'` or `'+'`.

- For example, in `"alice@neetcode.io"`, `"alice"` is the **local name**, and `"neetcode.io"` is the **domain name**.

If you add periods `'.'` between some characters in the **local name** part of an email address, mail sent there will be forwarded to the same address without dots in the local name. Note that this rule **does not apply** to **domain names**.

- For example, `"alice.z@neetcode.io"` and `"alicez@neetcode.io"` forward to the same email address.

If you add a plus `'+'` in the **local name**, everything after the first plus sign **will be ignored**. This allows certain emails to be filtered. Note that this rule **does not apply** to **domain names**.

- For example, `"m.y+name@email.com"` will be forwarded to `"my@email.com"`.  
    It is possible to use both of these rules at the same time.

You are given an array of strings `emails` where we send one email to each `emails[i]`, return the number of different addresses that actually receive mails.

**Example 1:**

```java
Input: emails = ["test.email+alex@neetcode.com","test.e.mail+bob.cathy@neetcode.com","testemail+david@nee.tcode.com"]

Output: 2
```

Explanation: `"testemail@neetcode.com"` and `"testemail@nee.tcode.com"` actually receive mails.

**Example 2:**

```java
Input: emails = ["a@neetcode.com","b@neetcode.com","c@neetcode.com"]

Output: 3
```

**Constraints:**

- `1 <= emails.length <= 100`
- `1 <= emails[i].length <= 100`
- `emails[i]` consist of lowercase English letters, `'+'`, `'.'` and `'@'`.
- Each `emails[i]` contains exactly **one** `'@'` character.
- All local and domain names are **non-empty**.
- Local names do not start with a `'+'` character.
- Domain names end with the `".com"` suffix.
- Domain names must contain at least one character before `".com"` suffix.

**Solutions:**

```python
class Solution:

    def numUniqueEmails(self, emails: List[str]) -> int:

        email_list = set()

  

        def get_true_email(email):

            local, add = email.split('@')

            res = []

  

            for c in local:

                if c == '+':

                    break

                if c != '.':

                    res.append(c + '@' + add)

  

            return ''.join(res)

  

        for email in emails:

            email_list.add(get_true_email(email))

  

        return len(email_list)
```

```python
class Solution:

    def numUniqueEmails(self, emails: List[str]) -> int:

        seen = set()

  

        for email in emails:

            name, address = email.split('@')

            name = name.split('+')[0].replace('.','')

            seen.add(name + '@' + address)

        return len(seen)
```