---
Difficulty: Easy
Topics: Arrays
---
# Range Sum Query Immutable

This is a part of [[LeetCode Patterns]].

You are given an integer array `nums`, handle multiple queries of the following type:

1. Calculate the **sum** of the elements of `nums` between indices `left` and `right` inclusive where `left <= right`.

Implement the `NumArray` class:

- `NumArray(int[] nums)` Initializes the object with the integer array `nums`.
    
- `int sumRange(int left, int right)` Returns the sum of the elements of `nums` between indices `left` and `right` inclusive (i.e. `nums[left] + nums[left + 1] + ... + nums[right]`).
    

**Example 1:**

```java
Input: ["NumArray","sumRange","sumRange","sumRange"]
[[[-2,0,3,-5,2,-1]],[0,2],[2,5],[0,5]]

Output: [null,1,-1,-3]
```

Explanation: NumArray numArray = new NumArray([-2, 0, 3, -5, 2, -1]);  
numArray.sumRange(0, 2); // return (-2) + 0 + 3 = 1  
numArray.sumRange(2, 5); // return 3 + (-5) + 2 + (-1) = -1  
numArray.sumRange(0, 5); // return (-2) + 0 + 3 + (-5) + 2 + (-1) = -3

**Constraints:**

- `1 <= nums.length <= 10,000`
- `-100,000 <= nums[i] <= 100,000`
- `0 <= left <= right < nums.length`
- At most 10,000 calls will be made to `sumRange`.

**Solutions:**

```python
class NumArray:

  

    def __init__(self, nums: List[int]):

        n = len(nums)

        self.prefixes = [0]*(n+1)

        for i in range(n):

            self.prefixes[i+1]= self.prefixes[i]+nums[i]

  

    def sumRange(self, left: int, right: int) -> int:

        return self.prefixes[right+1] - self.prefixes[left]

  
  

# Your NumArray object will be instantiated and called as such:

# obj = NumArray(nums)

# param_1 = obj.sumRange(left,right)
```

```python
class NumArray:

  

    def __init__(self, nums: List[int]):

        self.prefixes = [0]

        for num in nums:

            self.prefixes.append(self.prefixes[-1] + num)

  

    def sumRange(self, left: int, right: int) -> int:

        return self.prefixes[right+1] - self.prefixes[left]

  
  

# Your NumArray object will be instantiated and called as such:

# obj = NumArray(nums)

# param_1 = obj.sumRange(left,right)
```