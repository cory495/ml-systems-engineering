# Schema-on-Write

Date: 2026-06-15

---

## 1. Problem

How do we ensure data consistency and structure at the time data is ingested?

Without validation, data can become inconsistent and hard to query.

---

## 2. Intuition

Schema-on-write means:

> “Define the structure before data is stored.”

Data must conform to a predefined schema before being written into the database.

---

## 3. How It Works

- Step 1: Define schema (tables, columns, types, constraints)
- Step 2: Validate incoming data against schema
- Step 3: Reject or transform invalid data
- Step 4: Store clean, structured data

---

## 4. Key Components

- Schema definition (DDL)
- Type constraints
- Validation rules
- Database enforcement layer

---

## 5. Tradeoffs

### Pros
- Strong data consistency
- Easier querying
- Better data integrity
- Optimized for OLTP systems

### Cons
- Less flexible
- Slower ingestion of diverse data
- Requires schema migrations

---

## 6. Scaling / Complexity

- Schema changes require migrations
- Write-time validation overhead
- Strong constraints improve downstream performance

---

## 7. Real Systems Usage

- PostgreSQL
- MySQL
- Oracle DB
- Traditional OLTP systems

---

## 8. Failure Modes

- Migration failures
- Schema rigidity blocking new data
- Ingestion bottlenecks

---

## 9. Related Concepts

[[Schema Design]]
[[Schema-on-Read]]
[[OLTP]]
[[Normalization]]

---

## 10. Summary

Schema-on-write enforces structure at ingestion time, ensuring clean and consistent data at the cost of flexibility and ingestion speed.