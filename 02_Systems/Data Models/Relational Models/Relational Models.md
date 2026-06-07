# Relational Models

Date: 2026-06-07

---

## 1. Problem
Relational models solve the problem of organizing and storing real-world data in computers.

---

## 2. Intuition
Relational models organize data into relational systems, like relations which are collections of tuples.

---

## 3. Key Components
- Relations
- Keys
- Data

---

## 4. Tradeoffs
**Pros:**
- Data integrity
- Standardized querying
- Elimination of redundancy

**Cons:**
- Scaling difficulties
- Rigidity
- Inefficiency with hierarchies

**When NOT to use it:**
- With unstructured or rapidly changing data
- With massive scale that needs fast manipulation
- With highly interconnected data
- With data that needs real-time read/write speeds

---

## 5. Real Systems Usage
Where this shows up in industry:
- SQL

---

## 6. Failure Modes
- Schema Migrations
	- Adding a new column with loads of rows can lock the table because relational models are highly structured and modifying them requires altering the data layout.
- Scaling Bottlenecks
	- Relational databases use joins and rely on indexes. As volume grows linearly, join complexity grows exponentially.
- There are many other ways SQL can result in failure modes such as application drift, index bloat and degradation, and concurrency and deadlocks.

---

## 7. Related Concepts

- down:: [[Object-Relational Mismatch]]
---

## 8. Interview Questions
- Why use this over document models? Standardized querying results in faster data manipulation, and rigid structure results in high data integrity.
- What breaks at scale? Reliance on JOINs can cause SQL systems to result in failures and break at scale.
- How would you design it? SQL databases should be designed with these bottlenecks in mind. For instance, all columns should be made at the beginning, special attention should be paid to the data types put into the model, and data that requires non-rigid manipulation should be avoided.

---

## 9. Summary (5 lines max)
Relational models are data models that use relations to store and organize data.