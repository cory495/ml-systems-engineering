# MapReduce Querying

Date: 2026-06-07

---

## 1. Definition

**MapReduce querying** is a distributed data processing model where computation is expressed using two user-defined functions:

- **Map**: transforms input records into intermediate key-value pairs
- **Reduce**: aggregates values grouped by key

It sits between **imperative programming** and **declarative query languages**, because it requires writing code, but within a structured framework.

---

## 2. Why It Matters

MapReduce was widely used for large-scale distributed data processing, especially at Google and in early NoSQL systems.

It is important because it:

- Enables processing of massive datasets across many machines
- Provides fault tolerance and parallel execution
- Bridges the gap between custom code and database queries
- Influenced modern distributed query systems and batch processing frameworks

However, it also highlighted limitations in usability compared to declarative query languages like SQL.

---

## 3. Key Ideas

### Map Function

- Runs once per input document
- Emits key-value pairs

### Reduce Function

- Aggregates values for each key
- Must be a pure function (no side effects)

### Key-Based Grouping

- Framework groups emitted key-value pairs
- Reduce runs once per key

### Distributed Execution

- Computation is automatically parallelized across machines

### Pure Functions

Map and reduce functions:

- Must only use input data
- Cannot perform external queries
- Must not have side effects

This allows safe parallel execution and retries.

---

## 4. Examples

### SQL Version (Shark Count Per Month)

```sql
SELECT date_trunc('month', observation_timestamp) AS observation_month,
       sum(num_animals) AS total_animals
FROM observations
WHERE family = 'Sharks'
GROUP BY observation_month;
```

---

### MapReduce Version (MongoDB)

```javascript
db.observations.mapReduce(
  function map() {
    var year  = this.observationTimestamp.getFullYear();
    var month = this.observationTimestamp.getMonth() + 1;

    emit(year + "-" + month, this.numAnimals);
  },

  function reduce(key, values) {
    return Array.sum(values);
  },

  {
    query: { family: "Sharks" },
    out: "monthlySharkReport"
  }
);
```

---

### Aggregation Pipeline (Modern NoSQL Style)

```javascript
db.observations.aggregate([
  { $match: { family: "Sharks" } },
  {
    $group: {
      _id: {
        year:  { $year: "$observationTimestamp" },
        month: { $month: "$observationTimestamp" }
      },
      totalAnimals: { $sum: "$numAnimals" }
    }
  }
]);
```

---

## 5. How It Is Achieved

MapReduce works in stages:

1. Input data is split across nodes
2. Map function runs on each record
3. Intermediate key-value pairs are emitted
4. System groups values by key
5. Reduce function aggregates each group
6. Final results are written to output storage

The system handles:

- Distribution
- Fault tolerance
- Parallel execution
- Data shuffling between nodes

---

## 6. Tradeoffs

### Advantages

- Highly scalable across distributed systems
- Automatic parallelization
- Fault tolerant
- Flexible (can run arbitrary code in map/reduce)
- Works well for batch processing

### Disadvantages

- Low-level and verbose compared to SQL
- Harder to write and reason about
- Requires coordination between map and reduce functions
- Limited optimization opportunities
- Often reinvented SQL-like abstractions (aggregation pipelines)

---

## 7. Related Concepts

- [[Query Languages]]
- [[Declarative Querying]]

---

## 8. Summary

MapReduce is a distributed programming model for processing large datasets using map and reduce functions. While powerful and scalable, it is lower-level than declarative query languages like SQL. Over time, systems like MongoDB’s aggregation pipeline have moved toward more declarative approaches, reflecting the advantages of letting the system optimize execution rather than requiring explicit procedural code.