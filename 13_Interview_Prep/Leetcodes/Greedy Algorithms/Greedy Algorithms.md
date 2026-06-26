---
Type: Interview
Created: 2026-06-26
Updated: 2026-06-26
tags:
  - greedy
  - algorithms
  - interview-prep
---

# Greedy Algorithms

## Core Idea
Greedy algorithms make the locally optimal choice at each step with the hope of reaching a global optimum.

---

## Key Properties
- No reconsideration of previous decisions
- Works when greedy-choice property holds
- Often proven via exchange arguments
- Requires sorting or priority selection

---

## Common Patterns

### 1. Interval Scheduling
Pick non-overlapping intervals greedily.

Examples:
- Meeting Rooms
- Non-overlapping Intervals

---

### 2. Sorting + Greedy Choice
Sort then make local decisions.

Examples:
- Merge Intervals
- Insert Interval
- Minimum Number of Arrows

---

### 3. Heap-Based Greedy
Use priority queues for dynamic selection.

Examples:
- Task Scheduler
- IPO Problem
- Merge K Lists (greedy variant)

---

### 4. Jump / Reachability
Make optimal jumps or expansions.

Examples:
- Jump Game
- Jump Game II

---

## Complexity Cheat Sheet
- Time: O(n log n) (sorting often required)
- Space: O(1) or O(n)

---

## Relevant Problems

### Easy

### Medium
- down:: [[Jump Game]]
- down:: [[Jump Game II]]
- down:: [[Hand of Straights]]
- down:: [[Gas Station]]
- down:: [[Maximum Subarray]]
- down:: [[Merge Triplets to Form Targets]]

### Hard