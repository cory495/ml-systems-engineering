# ML Systems Dashboard

## Core Domains

### 04 Distributed Systems
```dataview
LIST  
FROM "04_Distributed_Systems"  
SORT file.name asc
```
### Databases
```dataview
LIST FROM "03_Databases"  
SORT file.name ASC
```
### Machine Learning Systems
```dataview
LIST FROM "07_ML_Systems"
SORT file.name ASC
```
### LLM Systems
```dataview
LIST FROM "08_LLM_Systems"
SORT file.name ASC
```

## Notes
### Recently Updated Notes
```dataview
TABLE file.mtime AS "Last Updated"
FROM ""
SORT file.mtime DESC
LIMIT 15
```
### In Progress
```dataview
LIST
FROM ""
WHERE status = "learning"
SORT file.name ASC
```
### Completed Concepts
```dataview
LIST
FROM ""
WHERE status = "complete"
SORT file.name ASC
```
## Papers
```dataview
LIST FROM "12_Papers"
SORT file.mtime DESC
```
## Projects
```dataview
LIST FROM "13_Projects"
SORT file.name ASC
```
