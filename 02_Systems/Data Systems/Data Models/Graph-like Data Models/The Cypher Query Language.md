# Cypher Query Language (Graph Queries)

Date: 2026-06-07

---

## 1. Definition

**Cypher** is a declarative query language designed for **property graphs**, primarily used in the Neo4j graph database.

It allows users to describe **graph patterns** they want to match rather than specifying how to traverse the graph step-by-step.

Cypher is named after _The Matrix_ character, not cryptographic ciphers.

---

## 2. Why It Matters

Cypher is important because it demonstrates how declarative querying extends naturally into graph data models.

It provides:

- A readable way to express graph patterns
    
- Declarative traversal of relationships
    
- Automatic query optimization
    
- Support for complex relationship queries (multi-hop traversal)
    

It shows that even graph databases benefit from SQL-like declarative abstractions.

---

## 3. Key Ideas

### Pattern Matching

Cypher queries describe patterns of nodes and relationships:

- `(A)-[:REL]->(B)` means A is connected to B by REL
    

### Named Nodes

Nodes can be assigned variables for reuse in queries:

- `(USA:Location {name:'United States'})`
    

### Relationship Types

Edges are labeled with relationship types:

- `BORN_IN`
    
- `LIVES_IN`
    
- `WITHIN`
    

### Variable-Length Paths

Cypher supports multi-hop traversal:

- `[:WITHIN*0..]` means “zero or more hops”
    

### Declarative Semantics

Users describe **what pattern exists**, not how to search for it.

---

## 4. Examples

### Data Creation (Graph Construction)

```cypher
CREATE
  (NAmerica:Location {name:'North America', type:'continent'}),
  (USA:Location      {name:'United States', type:'country'}),
  (Idaho:Location    {name:'Idaho', type:'state'}),
  (Lucy:Person       {name:'Lucy'}),

  (Idaho)-[:WITHIN]->(USA),
  (USA)-[:WITHIN]->(NAmerica),

  (Lucy)-[:BORN_IN]->(Idaho)
```

---

### Query: Find Emigrants (US → Europe)

```cypher
MATCH
  (person)-[:BORN_IN]->() -[:WITHIN*0..]-> (us:Location {name:'United States'}),
  (person)-[:LIVES_IN]->() -[:WITHIN*0..]-> (eu:Location {name:'Europe'})
RETURN person.name
```

---

## 5. How It Is Achieved

When executing a Cypher query:

1. The query is parsed into a graph pattern
    
2. The optimizer evaluates possible execution strategies
    
3. It may:
    
    - Start from known nodes (e.g., indexed locations like "United States")
        
    - Traverse relationships forward or backward
        
4. The engine chooses the most efficient traversal plan
    
5. The matching results are returned
    

Important insight: multiple execution strategies are possible, but the user does not specify them.

---

## 6. Tradeoffs

### Advantages

- Very expressive for graph traversal
    
- Intuitive visual mapping to graph structures
    
- Declarative (focus on patterns, not algorithms)
    
- Optimizable by the database engine
    
- Supports complex relationship queries easily
    

### Disadvantages

- Less standardized than SQL
    
- Performance depends heavily on query planning
    
- Can become complex with deeply nested patterns
    
- Specific to graph databases (less portable)
    

---

## 7. Related Concepts

- [[Graph-like Data Models]]
    
- [[Declarative Querying]]
    
- [[Query Languages]]
    
- [[Property Graphs]]
    
- [[The SPARQL Query Language]]
    
- [[Datalog]]

---

## 8. Summary

Cypher is a declarative query language for property graphs that allows users to express graph patterns instead of traversal logic. It enables powerful multi-hop relationship queries while letting the database decide how to execute them efficiently. This reinforces the broader DDIA theme: **separating what you want from how to compute it leads to better optimization and simpler applications**.