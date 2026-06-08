# RDF Data Model

Date: 2026-06-07

---

## 1. Definition

The **RDF (Resource Description Framework) data model** represents data as simple statements about resources in the form of:

**subject → predicate → object**

These statements are called **triples**.

Each triple describes a fact, such as:
- “Lucy lives in London”
- “Idaho is within the United States”

---

## 2. Why It Matters

RDF is important because it provides:

- A simple, universal way to represent data
- A foundation for graph-based knowledge systems
- A standard model for data integration across systems
- The basis for the Semantic Web

It is designed to support data that is:
- Highly connected
- Heterogeneous
- Distributed across different sources

---

## 3. Key Ideas

### Triples

All data is expressed as:

(subject, predicate, object)

Example:
(Lucy, lives_in, London)

---

### Graph Interpretation

RDF data naturally forms a graph:

- Subjects and objects are nodes
- Predicates are directed edges

---

### URIs

Entities are often identified using **URIs**, making them globally unique.

---

### Schema Flexibility

There is no fixed schema required; new relationships can be added freely.

---

## 4. Examples

(Lucy, born_in, Idaho)  
(Idaho, within, United_States)  
(United_States, within, North_America)

---

## 5. How It Is Achieved

RDF systems store triples in specialized databases or graph stores.

Queries involve:
- Matching patterns of triples
- Traversing relationships
- Filtering based on predicates or values

---

## 6. Tradeoffs

### Advantages
- Simple, uniform structure
- Flexible schema
- Well-suited for integration of diverse datasets
- Foundation for Semantic Web technologies

### Disadvantages
- Can become verbose
- Query performance depends on indexing
- Less intuitive for traditional tabular data
- Requires careful URI management

---

## 7. Related Concepts

- [[Graph-like Data Models]]
- [[Triple-Stores]]
- [[The SPARQL Query Language]]
- [[The Semantic Web]]
- [[Property Graphs]]

---

## 8. Summary

The RDF data model represents all information as triples, forming a graph of subject–predicate–object relationships. This simple structure enables flexible, distributed, and interoperable data representation, forming the foundation of the Semantic Web.