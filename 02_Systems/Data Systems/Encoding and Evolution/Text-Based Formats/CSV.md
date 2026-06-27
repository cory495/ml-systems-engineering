---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - distributed-systems
  - data-representation
  - encoding
Type: Notes
---

# CSV

Date: 2026-06-27

---

## 1. Problem

CSV (Comma-Separated Values) is a simple format for representing tabular data in plain text. It solves the problem of exporting and exchanging structured table-like data between systems in a minimal, universal format.

It is commonly used when data naturally fits into rows and columns, such as spreadsheets or simple datasets.

Without CSV, many simple data exchange workflows (spreadsheets, exports, analytics pipelines) would require heavier formats.

---

## 2. Intuition

CSV is the simplest possible representation of a table:

- Each line = a row
- Each comma-separated value = a column

It is essentially a flattened spreadsheet stored as text.

Its simplicity makes it extremely portable but also limits its ability to represent complex or nested structures.

---

## 3. How It Works

1. Data is organized into rows and columns.
2. Each row is written as a line in a text file.
3. Values are separated by commas (or other delimiters like tabs).
4. Optional quoting handles special characters.
5. The file is read line-by-line and parsed into a table structure.

---

## 4. Key Components

### Rows
Each line represents a record.

### Columns
Comma-separated fields within each row.

### Delimiters
Usually commas, but can also be semicolons or tabs.

### Parser
Converts text rows into structured tabular data.

---

## 5. Tradeoffs

### Pros

- Extremely simple format
- Universally supported
- Easy to generate and parse
- Works well with spreadsheet tools
- Low overhead for flat data

### Cons

- No type system
- No nested structures
- Ambiguous formatting rules
- Poor handling of large or complex datasets
- No schema enforcement

### When NOT to use it

Avoid CSV for complex hierarchical data, large-scale distributed systems, or when schema enforcement and type safety are required.

---

## 6. Scaling / Complexity

- Time: O(n) parsing
- Space: O(n)

Bottlenecks:
- string parsing
- escaping/quoting overhead
- lack of structure for optimization

---

## 7. Real Systems Usage

- Data exports from databases
- ETL pipelines
- Spreadsheet applications (Excel, Google Sheets)
- Simple analytics workflows
- Machine learning dataset preprocessing

---

## 8. Failure Modes

- Misinterpreted delimiters inside values
- Inconsistent schemas across rows
- Type ambiguity (everything is string)
- Encoding issues (UTF-8 vs others)
- Broken parsing due to malformed rows

---

## 9. Related Concepts

[[Serialization]]
[[Deserialization]]
[[Data Encoding Formats]]
[[JSON]]
[[XML]]

---

## 10. Interview Questions

- Why is CSV still widely used despite its limitations?
- What are the drawbacks of CSV compared to JSON?
- How do you handle commas inside values?
- Why is schema enforcement important for tabular data?
- When would you choose CSV over more structured formats?

---

## 11. Summary

CSV is a minimal, text-based format for representing tabular data. It is simple, universal, and widely supported, making it ideal for data exchange and spreadsheet workflows. However, it lacks schema enforcement, type safety, and support for complex structures, limiting its use in modern distributed systems and large-scale data pipelines.