---
Type: Interview
Created: 2026-06-26
Updated: 2026-06-26
tags:
  - intervals
  - greedy
  - sorting
  - interview-prep
---

# Intervals

## Core Idea
Interval problems involve ranges `[start, end]` and typically require sorting + merging, or greedy selection based on endpoints.

---

## Key Properties
- Sorting by start or end is essential
- Overlap detection is central
- Often reduced to greedy scheduling problems
- Sweep-line logic frequently applies

---

## Common Patterns

### 1. Merge Intervals
Combine overlapping intervals.

---

### 2. Insert Interval
Maintain sorted non-overlapping structure.

---

### 3. Overlap Detection
Check conflicts between intervals.

---

### 4. Sweep Line Technique
Convert intervals into events.

---

## Core Techniques

- Sort by start or end time
- Maintain current interval window
- Use greedy endpoint updates

---

## Complexity Cheat Sheet
- Time: O(n log n) due to sorting
- Space: O(n)

## Relevant Problems

### Easy
- [[Meeting Rooms]]