# Network Models

Date: 2026-06-07

---

## 1. Definition

The **network model** is a database model developed by the CODASYL (Conference on Data Systems Languages) committee. It extends the hierarchical model by allowing records to have **multiple parents**, enabling many-to-one and many-to-many relationships.

Instead of using foreign keys, records are connected through pointer-like links that form a network structure.

---

## 2. Why It Matters

The network model was one of the first database models capable of representing complex relationships between records.

It solved a major limitation of the hierarchical model, where each record could only have one parent. This made it possible to represent real-world relationships such as students enrolled in multiple courses or users belonging to shared regions.

The model also highlighted the challenges of tightly coupling data storage with data access, influencing the development of relational databases.

---

## 3. Key Ideas

### Multiple Parents

A record can have more than one parent record.

### Access Paths

Data is retrieved by traversing predefined paths through linked records.

### Pointer-Based Relationships

Relationships are stored as physical links between records.

### Navigational Queries

Queries require moving through records one at a time and following links.

### Many-to-Many Relationships

The model naturally supports many-to-many relationships.

### CODASYL Standard

The model was standardized by the Conference on Data Systems Languages (CODASYL).

---

## 4. Examples

### Geographic Regions

A region record may be connected to many users.

### Student Enrollment

Students and courses can have many-to-many relationships.

### Product Categories

Products may belong to multiple categories.

---

## 5. How It Is Achieved

The network model stores relationships as physical pointers between records.

To retrieve data:

1. Start from a known root record.
    
2. Follow an access path.
    
3. Traverse links until the desired record is found.
    

Queries are performed by:

- Moving a cursor through records.
    
- Following pointer chains.
    
- Explicitly navigating relationships in application code.
    

Programmers must understand and manage all available access paths.

---

## 6. Tradeoffs

### Advantages

- Supports many-to-many relationships.
    
- More flexible than the hierarchical model.
    
- Efficient on limited hardware.
    
- Direct pointer traversal can be very fast.
    

### Disadvantages

- Query logic becomes complex.
    
- Application code must manage navigation paths.
    
- Tight coupling between data structure and application code.
    
- Schema changes often require extensive code rewrites.
    
- Difficult to maintain and evolve.
    

---

## 7. Related Concepts

- [[Relational Models]]
    
- [[Many-to-One and Many-to-Many Relationships]]
    
- [[Data Models]]
    

---

## 8. Summary

The network model is an extension of the hierarchical model that allows records to have multiple parents through pointer-based relationships. Data is accessed by navigating predefined access paths rather than using declarative queries. While efficient for early computer systems, the model produced complex and inflexible application code, leading to the rise of relational databases.