```python
class Solution:

    def mergeTriplets(self, triplets: List[List[int]], target: List[int]) -> bool:

        found = [0] * 3

        for i in range(3):

            for trip in triplets:

                if trip[i] == target[i] and \

                trip[(i+1)%3] <= target[(i+1)%3] and \

                trip[(i+2)%3] <= target[(i+2)%3]:

                    found[i] = 1

                    break

        return sum(found) == 3
```

```python
class Solution:

    def mergeTriplets(self, triplets: List[List[int]], target: List[int]) -> bool:

        found = [0] * 3

        for a, b, c in triplets:

            if a > target[0] or b > target[1] or c > target[2]:

                continue

            if a == target[0]:

                found[0] = 1

            if b == target[1]:

                found[1] = 1

            if c == target[2]:

                found[2] = 1

        return sum(found) == 3
```