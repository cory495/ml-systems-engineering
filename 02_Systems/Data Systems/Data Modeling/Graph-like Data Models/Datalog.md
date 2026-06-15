# Datalog

Date: 2026-06-07

---

## 1. Definition

**Datalog** is a declarative query language based on logic programming.

It expresses data and queries using:

- **Facts** (base data)
- **Rules** (logical derivations)
- **Queries** (questions over facts + rules)

It is a subset of Prolog and forms a foundational model for modern graph query languages like Cypher and SPARQL.

---

## 2. Why It Matters

Datalog is important because it:

- Provides a formal foundation for graph query languages
- Supports recursive queries naturally
- Enables reusable logical rules
- Has strong ties to database theory and optimization research
- Is being revisited for parallel and distributed systems

It is especially relevant for:
- Knowledge graphs
- Rule-based systems
- Distributed query evaluation
- Static analysis and program reasoning

---

## 3. Key Ideas

### Facts

Data is represented as simple predicates:

- name(usa, 'United States')
- within(idaho, usa)

---

### Rules

Rules define new derived predicates:

migrated(...) :- conditions.

Rules can depend on:
- base facts
- other rules
- recursive definitions

---

### Recursion

Datalog supports recursive logic naturally, allowing:

- transitive closure (e.g., “within” hierarchy)
- graph traversal
- reachability queries

---

### Logical Variables

Variables (capitalized) are bound through pattern matching.

Example:
name(Location, Name)

---

## 4. Examples

### Base Facts

```
name(namerica, 'North America')
type(namerica, continent)

name(usa, 'United States')
type(usa, country)

within(usa, namerica)

name(idaho, 'Idaho')
type(idaho, state)

within(idaho, usa)

name(lucy, 'Lucy')
born_in(lucy, idaho)
```

---

### Recursive Rule: Location Hierarchy

```
within_recursive(Location, Name) :- name(Location, Name).
within_recursive(Location, Name) :- within(Location, Via),
                                    within_recursive(Via, Name).
```

---

### Query Rule: Migration

```
migrated(Name, BornIn, LivingIn) :-
    name(Person, Name),
    born_in(Person, BornLoc),
    within_recursive(BornLoc, BornIn),
    lives_in(Person, LivingLoc),
    within_recursive(LivingLoc, LivingIn).
```

---

### Query

```
?- migrated(Who, 'United States', 'Europe').
```

Result:
Who = 'Lucy'

---

## 5. How It Is Achieved

Datalog execution works by:

1. Storing base facts in a database
2. Applying rules to derive new facts
3. Repeating until no new facts can be inferred
4. Evaluating queries over the resulting fact set

This process is often called:

- **fixpoint computation**
- **rule evaluation**
- **bottom-up inference**

---

## 6. Tradeoffs

### Advantages

- Very expressive for recursive queries
- Clean logical semantics
- Rules are reusable and composable
- Strong theoretical foundation
- Well-suited for graph traversal and reasoning

### Disadvantages

- Less intuitive for simple ad-hoc queries
- Requires logical thinking style
- Not as widely adopted in industry
- Performance depends on evaluation strategy

---

## 7. Related Concepts

- [[Graph-like Data Models]]
- [[The SPARQL Query Language]]
- [[The Cypher Query Language]]
- [[Triple-Stores]]
- [[The Semantic Web]]
- [[Query Languages]]

---

## 8. Summary

Datalog is a declarative logic-based query language where queries are expressed as facts and rules. Its support for recursion makes it powerful for graph-like data and transitive relationships. It serves as a theoretical foundation for modern graph query languages and is increasingly relevant for distributed and parallel query systems.