# Schema-on-Read

Date: 2026-06-15

---

## 1. Definition

Data structure is interpreted when data is read rather than enforced when written.

---

## 2. Why It Matters

Allows flexible data storage without requiring strict predefined schemas.

---

## 3. Key Ideas

- Flexible structure
- Common in NoSQL systems
- Validation occurs later
- Supports evolving data

---

## 4. Examples

MongoDB documents with different fields:

```json
{ "name": "Alice" }

{ "name": "Bob", "age": 25 }
```

---

## 5. How It Is Achieved

Store raw data.
Interpret structure during queries.

---

## 6. Tradeoffs

### Pros

- Flexibility
- Easy schema evolution

### Cons

- Harder validation
- Messier data

---

## 7. Related Concepts

- [[Document Models]]
- [[Schema-on-Write]]
- [[NoSQL]]

---

## 8. Summary

Schema-on-read postpones structure enforcement until query time, increasing flexibility at the cost of consistency.