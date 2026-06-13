---
Difficulty: Easy
Topics: Two Pointers
---
# Merge Two 2D Arrays by Summing Values

This is a part of [[LeetCode Patterns]].

You are given two **2D** integer arrays `nums1` and `nums2.`

- `nums1[i] = [idi, vali]` indicate that the number with the id `idi` has a value equal to `vali`.
- `nums2[i] = [idi, vali]` indicate that the number with the id `idi` has a value equal to `vali`.

Each array contains **unique** ids and is sorted in **ascending** order by id.

Merge the two arrays into one array that is sorted in ascending order by id, respecting the following conditions:

- Only ids that appear in at least one of the two arrays should be included in the resulting array.
- Each id should be included **only once** and its value should be the sum of the values of this id in the two arrays. If the id does not exist in one of the two arrays, then assume its value in that array to be `0`.

Return _the resulting array_. The returned array must be sorted in ascending order by id.

**Constraints:**

- `1 <= nums1.length, nums2.length <= 200`
- `nums1[i].length == nums2[j].length == 2`
- `1 <= idi, vali <= 1000`

**Solutions:**

```python
class Solution:

    def mergeArrays(self, nums1: List[List[int]], nums2: List[List[int]]) -> List[List[int]]:

        i, j = 0, 0

        n, m = len(nums1), len(nums2)

  

        res = []

        while i < n and j < m:

            num1 = nums1[i]

            num2 = nums2[j]

  

            if num1[0] < num2[0]:  

                res.append(num1)

                i += 1

            elif num2[0] < num1[0]:

                res.append(num2)

                j += 1

            else:

                val = num1[1] + num2[1]

                res.append([num1[0], val])

                i += 1

                j += 1

        res.extend(nums1[i:n])

        res.extend(nums2[j:m])

        return res
```