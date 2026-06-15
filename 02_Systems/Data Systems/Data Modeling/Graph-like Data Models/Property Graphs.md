# Property Graphs

Date: 2026-06-07

---

## 1. Definition

A **property graph** is a graph data model where both **vertices (nodes)** and **edges (relationships)** can store structured data as **key-value pairs (properties)**.

It is one of the most common graph representations used in modern graph databases (e.g., Neo4j).

---

## 2. Why It Matters

Property graphs are important because they combine:

- Flexible schema design
    
- Rich relationship modeling
    
- Efficient graph traversal
    
- Support for heterogeneous data types
    

They make it possible to model complex, evolving systems where relationships are as important as the data itself.

This makes them especially useful for:

- Social networks
    
- Recommendation systems
    
- Knowledge graphs
    
- Fraud detection systems
    

---

## 3. Key Ideas

### Vertices (Nodes)

Each vertex contains:

- A unique identifier
    
- Outgoing edges
    
- Incoming edges
    
- A set of properties (key-value pairs)
    

### Edges (Relationships)

Each edge contains:

- A unique identifier
    
- A tail vertex (start node)
    
- A head vertex (end node)
    
- A label describing the relationship type
    
- A set of properties (key-value pairs)
    

---

### Schema Flexibility

There is no strict schema enforcing what can connect to what.

Any vertex can connect to any other vertex.

---

### Edge Labels

Edges are typed using labels such as:

- `FRIENDS_WITH`
    
- `BORN_IN`
    
- `LIVES_IN`
    
- `WITHIN`
    

This allows multiple relationship types in the same graph.

---

### Bidirectional Traversal

Because edges store both head and tail vertices, the system can efficiently traverse:

- Outgoing edges
    
- Incoming edges
    

This supports flexible navigation through the graph.

---

## 4. Examples

### Relational Representation of a Property Graph

A property graph can be represented using two tables:

```sql
CREATE TABLE vertices (
    vertex_id   integer PRIMARY KEY,
    properties  json
);

CREATE TABLE edges (
    edge_id     integer PRIMARY KEY,
    tail_vertex integer REFERENCES vertices (vertex_id),
    head_vertex integer REFERENCES vertices (vertex_id),
    label       text,
    properties  json
);

CREATE INDEX edges_tails ON edges (tail_vertex);
CREATE INDEX edges_heads ON edges (head_vertex);
```

---

### Example Conceptual Structure

Lucy (Person)

- BORN_IN → Idaho (State)
    
- LIVES_IN → London (City)
    

Idaho

- WITHIN → United States
    
- WITHIN → North America
    

---

### Extending the Graph (Example: Food Allergies)

Person → ALLERGIC_TO → Allergen → FOUND_IN → Food

This enables queries like:

- “What foods are safe for this person?”
    

---

## 5. How It Is Achieved

Property graph systems typically store:

- Nodes in a vertex store
    
- Edges in an edge store
    

Traversal is achieved by:

1. Looking up a vertex
    
2. Fetching its incoming/outgoing edges via indexes
    
3. Following edges to adjacent vertices
    
4. Repeating for multi-hop queries
    

Indexes on:

- `tail_vertex`
    
- `head_vertex`
    

enable efficient traversal in both directions.

---

## 6. Tradeoffs

### Advantages

- Highly flexible schema
    
- Natural modeling of complex relationships
    
- Efficient traversal of connected data
    
- Supports heterogeneous data in one graph
    
- Easy to evolve schema over time
    

### Disadvantages

- Less rigid structure than relational models
    
- Query optimization is more complex
    
- Harder to enforce constraints
    
- Can become difficult to reason about at scale
    
- Not ideal for purely tabular or aggregate-heavy workloads
    

---

## 7. Related Concepts

- [[Graph-like Data Models]]
    
- [[The Cypher Query Language]]
    
- [[The SPARQL Query Language]]
    
- [[Datalog]]
    
- [[Relational Models]]
    
- [[NoSQL]]

---

## 8. Summary

Property graphs store data as nodes and edges with flexible key-value properties on both. This design enables highly expressive and adaptable modeling of complex, interconnected data. By removing strict schema constraints and supporting rich relationship types, property graphs make it easy to evolve applications while maintaining powerful traversal capabilities.