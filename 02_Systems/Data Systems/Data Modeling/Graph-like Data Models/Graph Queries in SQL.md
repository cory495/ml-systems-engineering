# Graph Queries in SQL

Date: 2026-06-07

---

## 1. Definition

**Graph queries in SQL** refer to expressing graph-like traversals (such as multi-hop relationships) using relational tables and SQL constructs.

Although SQL is not designed for graph traversal, graph structures can be represented in relational tables and queried using techniques such as:

- Joins
    
- Recursive common table expressions (CTEs)
    
- Self-referential queries
    

---

## 2. Why It Matters

Graph queries in SQL show that:

- Graph data can be represented relationally
    
- SQL is expressive enough to simulate graph traversal
    
- However, graph-style queries are more complex in SQL than in graph query languages
    

This highlights a key DDIA theme:

> Data models influence how naturally certain queries can be expressed.

It also demonstrates why specialized graph query languages (e.g., Cypher) exist.

---

## 3. Key Ideas

### Fixed vs Variable Joins

- SQL joins are typically **fixed in number**
    
- Graph traversals often require **variable-length paths**
    

This mismatch makes graph queries harder in SQL.

---

### Recursive Queries

SQL:1999 introduced:

- **Recursive Common Table Expressions (WITH RECURSIVE)**
    

This allows:

- Iterative traversal of relationships
    
- Multi-hop graph-like queries
    

---

### Graph as Relational Tables

Graphs can be modeled as:

- `vertices` table (nodes)
    
- `edges` table (relationships)
    

Edges define connections between vertices via IDs.

---

### Traversal as Set Expansion

Graph traversal in SQL works by:

- Starting from a seed set
    
- Recursively expanding connected nodes
    
- Building intermediate sets
    

---

## 4. Example

### Recursive Graph Query (Emigration Example)

Find people born in the US and living in Europe:

```sql
WITH RECURSIVE in_usa(vertex_id) AS (
    SELECT vertex_id
    FROM vertices
    WHERE properties->>'name' = 'United States'

    UNION

    SELECT edges.tail_vertex
    FROM edges
    JOIN in_usa ON edges.head_vertex = in_usa.vertex_id
    WHERE edges.label = 'within'
),

in_europe(vertex_id) AS (
    SELECT vertex_id
    FROM vertices
    WHERE properties->>'name' = 'Europe'

    UNION

    SELECT edges.tail_vertex
    FROM edges
    JOIN in_europe ON edges.head_vertex = in_europe.vertex_id
    WHERE edges.label = 'within'
),

born_in_usa(vertex_id) AS (
    SELECT edges.tail_vertex
    FROM edges
    JOIN in_usa ON edges.head_vertex = in_usa.vertex_id
    WHERE edges.label = 'born_in'
),

lives_in_europe(vertex_id) AS (
    SELECT edges.tail_vertex
    FROM edges
    JOIN in_europe ON edges.head_vertex = in_europe.vertex_id
    WHERE edges.label = 'lives_in'
)

SELECT vertices.properties->>'name'
FROM vertices
JOIN born_in_usa
    ON vertices.vertex_id = born_in_usa.vertex_id
JOIN lives_in_europe
    ON vertices.vertex_id = lives_in_europe.vertex_id;
```

---

## 5. How It Works

This query works in stages:

### 1. Seed Sets

- Identify starting nodes (e.g., United States, Europe)
    

### 2. Recursive Expansion

- Follow `within` edges repeatedly
    
- Expand sets of reachable vertices
    

### 3. Relationship Mapping

- Find people connected via:
    
    - `born_in`
        
    - `lives_in`
        

### 4. Set Intersection

- Combine results using joins
    

---

## 6. Tradeoffs

### Advantages

- Graph data can be stored in relational systems
    
- SQL is widely supported
    
- Recursive CTEs enable graph-like traversal
    
- Unified system for multiple data types
    

### Disadvantages

- Verbose and complex queries
    
- Harder to express naturally than graph query languages
    
- Performance depends heavily on joins and recursion
    
- Less intuitive for deep or variable-length traversals
    

---

## 7. Graph Databases vs CODASYL

Graph databases are often compared to the older **CODASYL network model**, but they differ significantly.

### Key Differences

#### 1. Schema Flexibility

- CODASYL: strict schema defines allowed relationships
    
- Graph DBs: any node can connect to any node
    

#### 2. Access Paths

- CODASYL: must traverse predefined paths
    
- Graph DBs: can access nodes directly or via indexes
    

#### 3. Ordering

- CODASYL: ordered record sets
    
- Graph DBs: no inherent ordering of edges/nodes
    

#### 4. Query Style

- CODASYL: imperative navigation
    
- Graph DBs: support declarative languages (Cypher, SPARQL)
    

---

## 8. Related Concepts

- [[Graph-like Data Models]]
    
- [[The Cypher Query Language]]
    
- [[The SPARQL Query Language]]
    
- [[Datalog]]
    
- [[Relational Models]]
    
- [[Data Models]]
    

---

## 9. Summary

Graph queries can be implemented in SQL using recursive common table expressions, allowing relational databases to simulate graph traversal. However, these queries are significantly more complex than in graph-specific query languages like Cypher. This illustrates a core idea in data systems: while models are often inter-convertible, some are far more natural and expressive for specific types of queries.