# Bit Manipulation

## Core Idea

Bit manipulation involves operating directly on the binary representation of integers using bitwise operators.

Many problems that appear to require loops, extra memory, or arithmetic tricks can often be solved more efficiently using binary operations.

---

## Binary Basics

### Decimal to Binary

```text
13 = 1101

8 4 2 1
1 1 0 1
```

Each position represents a power of 2.

---

### Common Bitwise Operators

| Operator | Name | Example |
|----------|------|----------|
| `&` | AND | `5 & 3 = 1` |
| `\|` | OR | `5 \| 3 = 7` |
| `^` | XOR | `5 ^ 3 = 6` |
| `~` | NOT | `~5 = -6` |
| `<<` | Left Shift | `5 << 1 = 10` |
| `>>` | Right Shift | `5 >> 1 = 2` |

---

## Important Patterns

### Check if a Bit is Set

Check whether the kth bit is 1.

```python
(n >> k) & 1
```

Example:

```python
n = 13  # 1101
k = 2

(n >> 2) & 1
```

Result:

```text
1
```

---

### Set a Bit

Turn the kth bit into 1.

```python
n |= (1 << k)
```

---

### Clear a Bit

Turn the kth bit into 0.

```python
n &= ~(1 << k)
```

---

### Toggle a Bit

Flip the kth bit.

```python
n ^= (1 << k)
```

---

## Power of Two

A power of two contains exactly one set bit.

```python
n > 0 and (n & (n - 1)) == 0
```

Examples:

```text
8  = 1000
16 = 10000
32 = 100000
```

---

## Count Set Bits (Hamming Weight)

### Brute Force

```python
count = 0

while n:
    count += n & 1
    n >>= 1
```

**Time Complexity:** O(log n)

---

### Brian Kernighan's Algorithm

```python
count = 0

while n:
    n &= (n - 1)
    count += 1
```

Each iteration removes the rightmost set bit.

Example:

```text
1011000
1010111
-------
1010000
```

**Time Complexity:** O(k)

where k = number of set bits.

---

## Rightmost Set Bit

Extract the lowest set bit.

```python
n & -n
```

Example:

```text
12 = 1100

1100
0100
-----
0100
```

Result:

```text
4
```

---

## Remove Rightmost Set Bit

```python
n &= (n - 1)
```

Example:

```text
1011000
1010111
-------
1010000
```

---

## XOR Properties

### Key Rules

```text
a ^ a = 0

a ^ 0 = a

a ^ b ^ a = b
```

---

### Find Single Number

Every element appears twice except one.

```python
ans = 0

for num in nums:
    ans ^= num

return ans
```

**Time Complexity:** O(n)

**Space Complexity:** O(1)

---

## Counting Bits

### Observation

```text
bits(i) = bits(i >> 1) + (i & 1)
```

The right shift removes the last bit.

The final bit contributes either:

0 or 1

---

### Dynamic Programming Solution

```python
class Solution:
    def countBits(self, n: int) -> List[int]:
        dp = [0] * (n + 1)

        for i in range(1, n + 1):
            dp[i] = dp[i >> 1] + (i & 1)

        return dp
```

**Time Complexity:** O(n)

**Space Complexity:** O(n)

---

## Common Interview Problems

### Easy

- Number of 1 Bits
- Counting Bits
- Reverse Bits
- Power of Two
- Single Number

### Medium

- Sum of Two Integers
- Bitwise AND of Numbers Range
- Subsets
- Single Number II
- Maximum XOR of Two Numbers

### Hard

- Minimum One Bit Operations
- Maximum XOR Queries
- Advanced Trie + XOR Problems

---

## Complexity Cheat Sheet

| Operation | Complexity |
|------------|------------|
| Check Bit | O(1) |
| Set Bit | O(1) |
| Clear Bit | O(1) |
| Toggle Bit | O(1) |
| Count Bits (shift) | O(log n) |
| Count Bits (Kernighan) | O(k) |
| Power of Two Check | O(1) |
| XOR Duplicate Removal | O(n) |

---

## Mental Models

- Right shift (`>> 1`) = divide by 2.
- Left shift (`<< 1`) = multiply by 2.
- XOR is useful when pairs cancel out.
- `n & (n - 1)` removes the lowest set bit.
- `n & -n` isolates the lowest set bit.
- Most bit problems become easier if you write the number in binary first.

## Relevant Problems

### Easy
- down:: [[Counting Bits]]
- down:: [[Number of One Bits]]