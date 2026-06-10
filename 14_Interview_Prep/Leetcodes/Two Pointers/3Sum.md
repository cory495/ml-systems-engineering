---
Difficulty: Medium
Topics: Two Pointers
---
# 3Sum

Given an integer array `nums`, return all the triplets `[nums[i], nums[j], nums[k]]` where `nums[i] + nums[j] + nums[k] == 0`, and the indices `i`, `j` and `k` are all distinct.

The output should _not_ contain any duplicate triplets. You may return the output and the triplets in **any order**.

**Example 1:**

```java
Input: nums = [-1,0,1,2,-1,-4]

Output: [[-1,-1,2],[-1,0,1]]
```

Explanation:  
`nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.`  
`nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.`  
`nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.`  
The distinct triplets are `[-1,0,1]` and `[-1,-1,2]`.

**Example 2:**

```java
Input: nums = [0,1,1]

Output: []
```

Explanation: The only possible triplet does not sum up to 0.

**Example 3:**

```java
Input: nums = [0,0,0]

Output: [[0,0,0]]
```

Explanation: The only possible triplet sums up to 0.

**Constraints:**

- `3 <= nums.length <= 1000`
- `-10^5 <= nums[i] <= 10^5`

**Solutions:**

```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        solutions = set()
        for i in range(len(nums)):
            for j in range(i+1, len(nums)):
                for k in range(j+1, len(nums)):
                    if nums[i]+nums[j]+nums[k]==0:
                        solutions.add(tuple(sorted([nums[i], nums[j], nums[k]])))
        return list(solutions)
```

The first solution was the naive approach of iterating three times. To optimize it further, the clearest path forward was using sliding windows on all values left for each index where there are enough values to choose two indices after it.
```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        n = len(nums)
        nums = sorted(nums)
        solutions = []
        
        for i in range(n - 2):
            if i > 0 and nums[i] == nums[i - 1]:
                continue
            
            left, right = i + 1, len(nums) - 1

            while left < right:
                sum_val = nums[left] + nums[i] + nums[right]
                if sum_val < 0:
                    left += 1
                elif sum_val > 0:
                    right -= 1
                else:
                    solutions.append([nums[left], nums[i], nums[right]])
                    while left < right and nums[left] == nums[left + 1]:
                        left += 1
                    while left < right and nums[right] == nums[right - 1]:
                        right -= 1
                    left += 1
                    right -= 1

        return solutions
```
