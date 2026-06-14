# Arrays

## Core Idea
An array is a contiguous block of memory that stores elements in indexed order. It allows O(1) access by index but has tradeoffs for insertion and deletion.

---

## Key Properties
- Fixed or dynamic size (Python lists are dynamic arrays)
- O(1) random access: arr[i]
- O(n) insert/delete (worst case due to shifting)

---

## Common Patterns

### 1. Traversal
- Iterate through all elements
- Used in most basic problems

---

### 2. Prefix Sum
Used to answer range sum queries efficiently.

```python
prefix[i] = sum(arr[0:i])
```

Range sum:
```python
prefix[r] - prefix[l-1]
```

---

### 3. [[Two Pointers]]
Used when array is sorted or needs pairing.

Examples:
- Two Sum (sorted)
- Container With Most Water
- Remove duplicates

---

### 4. In-place Modification
Modify array without extra space.

Examples:
- Move zeroes
- Remove element
- Rotate array

---

### 5. Partitioning
Split array into segments.

Examples:
- QuickSort partition logic
- Dutch National Flag problem

---

## Common Interview Problems
- Two Sum
- Best Time to Buy/Sell Stock
- Product of Array Except Self
- Maximum Subarray (Kadane’s Algorithm)

---

## Complexity Cheat Sheet
- Access: O(1)
- Search: O(n)
- Insert (middle): O(n)
- Delete (middle): O(n)

---
## Relevant Problems
### Easy
- down:: [[Contains Duplicate]]
- down:: [[Two Sum]]
- down:: [[Valid Anagram]]
- down:: [[Get Concatenation of Array]]
- down:: [[Replace Elements With Greatest Element On Right Side]]
- down:: [[Is Subsequence]]
- down:: [[Score of a String]]
- down:: [[Length of Last Word]]
- down:: [[Number of Senior Citizens]]
- down:: [[Max Consecutive Ones]]
- down:: [[Longest Common Prefix]]
- down:: [[String Matching in Array]]
- down:: [[Can Place Flowerbeds]]
- down:: [[Best Time to Buy and Sell Stock II]]
- down:: [[Isomorphic Strings]]
- down:: [[Merge Sorted Array]]
- down:: [[Pascal's Triangle]]
- down:: [[Remove Element]]
- down:: [[Unique Email Addresses]]
- down:: [[Majority Element]]
- down:: [[Maximum Difference Between Even and Odd Frequency I]]
- down:: [[Longest Palindrome]]
- down:: [[Range Sum Query Immutable]]
### Medium
- down:: [[Group Anagrams]]
- down:: [[Top K Frequent Elements]]
- down:: [[Encode and Decode Strings]]
- down:: [[# Products of Array Except Self]]
- down:: [[Valid Sudoku]]
- down:: [[Longest Consecutive Sequence]]
- down:: [[Append Characters to String to Make Subsequence]]
- down:: [[Average Waiting Time]]
- down:: [[Custom Sort String]]
- down:: [[Range Sum Query 2D Immutable]]
- down:: [[Sort Colors]]
- down:: [[Count Vowel Strings in Ranges]]
- down:: [[Majority Element II]]