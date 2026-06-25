```python
# The guess API is already defined for you.

# @param num, your guess

# @return -1 if num is higher than the picked number

#          1 if num is lower than the picked number

#          otherwise return 0

# def guess(num: int) -> int:

  

class Solution:

    def guessNumber(self, n: int) -> int:

        l, r = 1, n

        num = (l+r) // 2

        while l <= r:

            num = (l+r) // 2

            status = guess(num)

            if status == -1:

                r = num - 1

            elif status == 1:

                l = num + 1

            elif status == 0:

                return num
```

```python
# The guess API is already defined for you.

# @param num, your guess

# @return -1 if num is higher than the picked number

#          1 if num is lower than the picked number

#          otherwise return 0

# def guess(num: int) -> int:

  

class Solution:

    def guessNumber(self, n: int) -> int:

        l, r = 1, n

        num = (l+r) // 2

        while True:

            num1 = l + (r-l) // 3

            num2 = r - (r-l) // 3

            status = guess(num)

            if guess(num1) == 0:

                return num1

            if guess(num2) == 0:

                return num2

            if guess(num1) + guess(num2) == 0:

                l = num1 + 1

                r = num2 - 1

            elif guess(num1) == -1:

                r = num1 - 1

            else:

                l = num2 + 1
```