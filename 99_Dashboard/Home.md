# ML Systems Dashboard
On DDIA Many-to-one and many-to-many relationships

## Core Domains

### Distributed Systems
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
## Architecture
```dataview
LIST FROM "10_Architecture"
SORT file.name ASC
```
## Systems Design
```dataview
LIST FROM "11_System_Design"
SORT file.name ASC
```