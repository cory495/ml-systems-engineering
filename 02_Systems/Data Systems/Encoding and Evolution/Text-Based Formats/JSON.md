---
Created: 2026-06-27
Updated: 2026-06-27
tags:
  - distributed-systems
  - data-representation
  - encoding
Type: Notes
---

# JSON

Date: 2026-06-27

---

## 1. Problem

JSON (JavaScript Object Notation) solves the problem of representing structured data in a lightweight, human-readable format that can be easily transmitted between systems and parsed across programming languages.

Before JSON-like formats became standard, systems relied on ad-hoc text formats or XML, which were often verbose and harder to work with. JSON provides a minimal syntax for representing objects, arrays, and primitive values in a way that is both machine-parseable and human-readable.

Without JSON:

- Web APIs would lack a universal data exchange format
- Frontend-backend communication would be inconsistent
- Debugging network payloads would be significantly harder

---

## 2. Intuition

JSON is essentially a standardized way of writing down structured data using plain text.

Think of it as a universal “data handwriting” that both humans and machines can understand.

It represents:
- Objects → key-value maps
- Arrays → ordered lists
- Primitives → strings, numbers, booleans, null

Its simplicity is its main strength: there is almost no ambiguity in how data is expressed.

---

## 3. How It Works

1. A data structure (object, dictionary, map) is created in memory.
2. A JSON serializer converts it into a text string.
3. Keys are quoted strings; values are recursively encoded.
4. Nested structures are represented using braces `{}` and brackets `[]`.
5. The resulting string is transmitted or stored.
6. A JSON parser reconstructs the original structure in memory.

---

## 4. Key Components

### Objects
Key-value pairs enclosed in `{}`.

### Arrays
Ordered sequences enclosed in `[]`.

### Primitives
- Strings
- Numbers
- Booleans
- Null

### Parser / Serializer
Responsible for converting between in-memory structures and JSON text.

---

## 5. Tradeoffs

### Pros

- Human-readable and easy to debug
- Universally supported across languages
- Lightweight compared to XML
- Ideal for APIs and configuration files

### Cons

- No native schema enforcement
- Larger payloads than binary formats
- Slower parsing compared to binary encodings
- No strong typing guarantees

### When NOT to use it

Avoid JSON in high-performance systems where bandwidth, latency, or strict schema enforcement matters (e.g., large-scale streaming systems or ML training pipelines).

---

## 6. Scaling / Complexity

- Time: O(n) parsing and serialization
- Space: O(n) with relatively high overhead due to text encoding

Bottlenecks:
- string parsing
- allocation overhead
- lack of binary compression

---

## 7. Real Systems Usage

- REST APIs (web and mobile communication)
- Configuration files (e.g., package configs)
- Logging systems
- NoSQL document databases (e.g., MongoDB-style storage models)
- Frontend-backend communication in web applications

---

## 8. Failure Modes

- Schema drift due to lack of enforcement
- Type ambiguity (e.g., numbers vs strings)
- Large payload inefficiency
- Silent errors from missing fields
- Parsing inconsistencies across languages

---

## 9. Related Concepts

[[Serialization]]
[[Deserialization]]
[[Data Encoding Formats]]
[[XML]]
[[CSV]]

---

## 10. Interview Questions

- Why is JSON widely used in web systems?
- What are the limitations of JSON compared to binary formats?
- How does JSON handle types and why is that a problem?
- When would you avoid using JSON?
- How does JSON affect system performance at scale?

---

## 11. Summary

JSON is a lightweight, human-readable data encoding format used for representing structured data as text. It is widely used in APIs, configuration files, and web communication due to its simplicity and universal support. However, it lacks schema enforcement and is less efficient than binary formats, making it less suitable for high-performance or large-scale distributed systems.