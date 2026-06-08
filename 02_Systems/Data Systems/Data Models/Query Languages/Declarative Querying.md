# Declarative Queries

Date: 2026-06-07

---

## 1. Definition

A **declarative query** specifies the desired result of a query without specifying the exact steps required to obtain that result.

The user describes:

- What data is needed
- What conditions must be satisfied
- How results should be presented

The database or execution engine determines how to retrieve the data efficiently.

---

## 2. Why It Matters

Declarative queries separate a user's intent from the implementation details of data retrieval.

This separation enables:

- Automatic query optimization
- Improved maintainability
- Greater flexibility
- Easier schema evolution
- Parallel execution strategies

The success of SQL is largely due to its declarative nature.

---

## 3. Key Ideas

### Describe the Result

The query specifies the desired output rather than the retrieval procedure.

### Execution Independence

Users do not control indexes, joins, traversal order, or execution plans.

### Query Optimization

The database optimizer chooses the most efficient execution strategy.

### Data Independence

Applications remain insulated from physical storage changes.

### Parallelism

Execution engines can distribute work across multiple cores or machines.

---

## 4. Examples

### SQL

Retrieve all sharks from a collection of animals.

```sql
SELECT *
FROM animals
WHERE family = 'Sharks';
```

The query specifies what records are desired but not how they should be found.

### Relational Algebra

```text
sharks = σfamily="Sharks"(animals)
```

The expression defines the result set without describing the retrieval algorithm.

### CSS

Apply a blue background to the title of a selected navigation item.

```css
li.selected > p {
    background-color: blue;
}
```

The browser determines which elements satisfy the selector.

### XPath / XSL

```xml
li[@class='selected']/p
```

The pattern identifies matching elements without describing the search process.

---

## 5. How It Is Achieved

A declarative query typically follows this process:

1. The user specifies a desired result.
2. The query is parsed.
3. An optimizer generates candidate execution plans.
4. The optimizer selects the most efficient plan.
5. The execution engine produces the result.

Because execution details are hidden, the underlying system can improve performance without requiring query changes.

---

## 6. Tradeoffs

### Advantages

- Shorter and easier to read.
- Less tightly coupled to implementation details.
- Enables automatic optimization.
- Easier to maintain.
- Supports parallel execution.
- Allows storage structures to evolve.

### Disadvantages

- Less control over execution behavior.
- Performance problems can be difficult to diagnose.
- Quality depends heavily on the optimizer.
- Some specialized operations may require procedural extensions.

---

## 7. Related Concepts

- [[Query Languages]]

---

## 8. Summary

Declarative queries describe what result is desired rather than how to obtain it. By separating query intent from execution details, declarative systems can optimize performance, adapt to storage changes, and execute operations in parallel. SQL, relational algebra, CSS, and XPath are all examples of declarative approaches that allow systems to determine the best execution strategy automatically.