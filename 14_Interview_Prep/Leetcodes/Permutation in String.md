**Solutions:**

```python
class Solution:
    def checkInclusion(self, s1: str, s2: str) -> bool:
        if len(s1) > len(s2):
            return False
            
        chars = [0] * 26
        
        def getIndex(c):
            return ord(c) - ord('a')
        
        # Count characters in s1
        for c in s1:
            chars[getIndex(c)] += 1
        
        left = 0
        for right in range(len(s2)):
            # Add current character
            chars[getIndex(s2[right])] -= 1
            
            # If window is too big, remove leftmost character
            if right - left + 1 > len(s1):
                chars[getIndex(s2[left])] += 1
                left += 1
            
            # Check if current window is a permutation
            if right - left + 1 == len(s1) and all(count == 0 for count in chars):
                return True
        
        return False
```
