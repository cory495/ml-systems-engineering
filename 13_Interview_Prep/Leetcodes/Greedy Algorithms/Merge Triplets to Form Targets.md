---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - interview
  - programming
Type: Interview
Difficulty: Medium
Topics: Greedy
---
# Merge Triplets to Form Targets

This is a part of [[LeetCode Patterns]].

You are given a 2D array of integers `triplets`, where `triplets[i] = [ai, bi, ci]` represents the `ith` **triplet**. You are also given an array of integers `target = [x, y, z]` which is the triplet we want to obtain.

To obtain `target`, you may apply the following operation on `triplets` zero or more times:

Choose two **different** triplets `triplets[i]` and `triplets[j]` and update `triplets[j]` to become `[max(ai, aj), max(bi, bj), max(ci, cj)]`.  
* E.g. if `triplets[i] = [1, 3, 1]` and `triplets[j] = [2, 1, 2]`, `triplets[j]` will be updated to `[max(1, 2), max(3, 1), max(1, 2)] = [2, 3, 2]`.

Return `true` if it is possible to obtain `target` as an **element** of `triplets`, or `false` otherwise.

**Example 1:**

```java
Input: triplets = [[1,2,3],[7,1,1]], target = [7,2,3]

Output: true
```

Explanation:  
Choose the first and second triplets, update the second triplet to be [max(1, 7), max(2, 1), max(3, 1)] = [7, 2, 3].

**Example 2:**

```java
Input: triplets = [[2,5,6],[1,4,4],[5,7,5]], target = [5,4,6]

Output: false
```

**Constraints:**

- `1 <= triplets.length <= 1000`
- `1 <= ai, bi, ci, x, y, z <= 100`

**Solutions:**

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