---
Created: 2026-06-01
Updated: 2026-06-26
tags:
  - 
Type: Dashboard
---
# Home

> *"Build something every day. Learn something every day."*

---

# Mission

**Long-Term Goal**

> Become a ML Engineer

Current Focus

- ML Systems
- LLM Systems
- Signal Processing
- Physical AI

---

# Current Semester

## Semester Goals

- [ ] Finish current coursework
- [ ] Read 30 papers
- [ ] Complete one major portfolio project

---

# Currently Reading

## Books

```dataview
TABLE
status AS "Status",
current_page + " / " + pages AS "Progress"
WHERE type = "book"
AND status = "Reading"
SORT priority DESC
```

---

## Papers

```dataview
TABLE
category,
year,
status
FROM "11_Papers"
WHERE type = "paper"
AND status = "Reading"
SORT priority DESC
```

---

## Courses

```dataview
TABLE
semester,
status
WHERE type = "course"
AND status != "Completed"
```

---

# Active Projects

```dataview
TABLE
completion + "%" AS "Progress",
priority,
status
FROM "12_Projects"
WHERE type = "project"
AND status != "Completed"
SORT priority DESC
```

---

# Active Research

```dataview
TABLE
conference,
deadline,
status
FROM "14_Research"
WHERE type = "research"
SORT deadline ASC
```

---

# Upcoming Deadlines

```dataview
TABLE deadline
WHERE deadline
SORT deadline ASC
LIMIT 10
```

---

# Recently Updated

```dataview
TABLE file.mtime AS "Modified"
FROM ""
SORT file.mtime DESC
LIMIT 15
```

---

# Progress

## Books

```dataview
TABLE WITHOUT ID
length(rows) AS "Reading"
FROM ""
WHERE type = "book"
AND status = "Reading"
GROUP BY true
```

## Papers

```dataview
TABLE WITHOUT ID
length(rows) AS "Completed"
FROM "11_Papers"
WHERE status = "Completed"
GROUP BY true
```

## Projects

```dataview
TABLE WITHOUT ID
length(rows) AS "Active"
FROM "12_Projects"
WHERE status = "Active"
GROUP BY true
```

---

# Knowledge

## Mathematics

```dataview
LIST
FROM "01_Mathematics"
SORT file.name ASC
```

---

## Systems

```dataview
LIST
FROM "02_Systems"
SORT file.name ASC
```

---

## Machine Learning

```dataview
LIST
FROM "03_Machine_Learning"
SORT file.name ASC
```

---

## Deep Learning

```dataview
LIST
FROM "04_Deep_Learning"
SORT file.name ASC
```

---

## ML Systems

```dataview
LIST
FROM "05_ML_Systems"
SORT file.name ASC
```

---

## LLM Systems

```dataview
LIST
FROM "06_LLM_Systems"
SORT file.name ASC
```

---

## GPU Systems

```dataview
LIST
FROM "07_GPU_Systems"
SORT file.name ASC
```

---

## Signal Processing

```dataview
LIST
FROM "08_Signal_Processing"
SORT file.name ASC
```

---

## Architecture Case Studies

```dataview
LIST
FROM "09_Architecture_Case_Studies"
SORT file.name ASC
```

---

## System Design

```dataview
LIST
FROM "10_System_Design"
SORT file.name ASC
```

---

# Papers

```dataview
LIST
FROM "11_Papers"
SORT file.name ASC
```

---

# Projects

```dataview
LIST
FROM "12_Projects"
SORT file.name ASC
```

---

# Interview Prep

```dataview
LIST
FROM "13_Interview_Prep"
SORT file.name ASC
```

---

# Research Ideas

- 

- 

- 

---

# Quick Links

- [[00_Roadmap]]
- [[14_Research]]
- [[15_Career]]
- [[99_Dashboard/Home]]