# Data Models

Date: 2026-06-07

---

## 1. Definition

A data model is a way of structuring and representing data in a system, defining how information is organized, stored, and accessed.

Data models are not just storage formats—they shape how applications are designed and how problems are reasoned about.

---

## 2. Why It Matters

The choice of data model strongly influences:

- How easy it is to express application logic
    
- How efficiently data can be queried or updated
    
- How systems scale and evolve over time
    
- How developers think about the problem domain
    

In practice, the data model often determines the shape of the entire application architecture.

---

## 3. Key Ideas

### Data models represent real-world concepts

Real-world entities are translated into structured representations:

- Users → records or documents
    
- Relationships → foreign keys or graph edges
    
- Events → logs or event streams
    
- Money flows → transactions
    

### Data models shape APIs

Applications don’t just store data—they _interact with data through the model_.

The data model directly influences API design and system boundaries.

### Main categories of data models

- **Relational model** (tables, rows, SQL)
    
- **Document model** (JSON, BSON, XML)
    
- **Graph model** (nodes and edges)
    
- **Key-value model** (simple lookup structure)
    
- **Wide-column / column-family model**
    

Each model optimizes for different types of access patterns and workloads.

---

## 4. Examples

### People as a Data Model

A user might be represented as:

- A row in a relational table
    
- A JSON document in a document store
    
- A node in a graph with relationships (friends, followers)
    

---

### Organizations

Organizations can be modeled with:

- Hierarchical relationships (org charts)
    
- Graph structures (complex ownership or reporting)
    
- Relational schemas (normalized structure)
    

---

### Event Streams

Actions such as clicks, purchases, or sensor readings can be modeled as:

- Append-only logs
    
- Event streams
    
- Time-series records
    

---

### Money Flows

Financial systems often use:

- Strongly structured relational models
    
- Transactional consistency guarantees
    
- Audit logs for traceability
    

---

## 5. How It Influences System Design

Data models affect:

- Query patterns (what is easy or hard to retrieve)
    
- Storage structure (indexes, partitions, replication)
    
- Application architecture (monolith vs services)
    
- Scalability strategies (denormalization, caching)
    

Choosing a data model is often equivalent to choosing a system design strategy.

---

## 6. Tradeoffs

Different data models involve tradeoffs such as:

- Flexibility vs performance
    
- Simplicity vs expressiveness
    
- Strong consistency vs availability
    
- Read efficiency vs write efficiency
    

No single data model is optimal for all workloads.

---

## 7. Related Concepts

down:: [[Relational Models]]  
down:: [[Document Models]]  
down:: [[Graph-like Data Models]]  
down:: [[NoSQL]]  
down:: [[Query Languages]]

[[Data Systems]]  
[[Scalability]]  
[[Performance]]  
[[Indexing]]  
[[Schema Design]]

---

## 8. Common Interview Questions

- What is a data model?
    
- Why does the choice of data model matter?
    
- When would you use a relational vs document model?
    
- What are the tradeoffs between SQL and NoSQL systems?
    
- How do data models affect scalability?
    
- What is schema design?
    

---

## 9. Summary

A data model is a structured way of representing and organizing data. It influences how systems are designed, how data is queried, and how applications evolve over time. Choosing the right data model is a fundamental decision in system design.