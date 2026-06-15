# Normalization

Date: 2026-06-15

---

## 1. Definition

Normalization is the process of organizing data into separate tables to minimize redundancy and maintain consistency.

---

## 2. Why It Matters

Without normalization, the same information may be stored in multiple places, making updates difficult and increasing the risk of inconsistencies.

---

## 3. Key Ideas

- Single source of truth
- Minimize duplicated data
- Separate entities into dedicated tables
- Use relationships through foreign keys

---

## 4. Examples

Bad:

Customer information repeated in every order record.

Good:

Customers table

Orders table

Orders reference customers via CustomerID.

---

## 5. How It Is Achieved

- First Normal Form (1NF)
- Second Normal Form (2NF)
- Third Normal Form (3NF)

Most production systems stop around 3NF.

---

## 6. Tradeoffs

### Pros

- Data consistency
- Reduced storage requirements
- Easier updates

### Cons

- More joins
- More complex queries

---

## 7. Related Concepts

- [[Denormalization]]
- [[Joins]]
- [[Relational Models]]

---

## 8. Summary

Normalization reduces redundancy by separating data into related tables. It improves consistency but often requires joins to reconstruct information.