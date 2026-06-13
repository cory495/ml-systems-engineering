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