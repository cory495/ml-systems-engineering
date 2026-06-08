# Object-Relational Mismatch

Date: 2026-06-07

---

## 1. Definition

---
An object-relational mismatch, sometimes called an impedance mismatch, is a mismatch between object-oriented programming and SQL data models that result in an awkward translational layer.
## 2. Why It Matters

---
This mismatch matters because it is one driving force pushing people to NoSQL.
## 3. Key Ideas

---
- JSON representations have better locality than multi-table schemas.
## 4. Examples

---
- Any code that has to convert the storage layer into the application code, like Python code to put the storage layer into a pandas dataframe.
![[pic_relational_linkedin.png]]
```JSON
{ "user_id": 251, 
	"first_name": "Bill", 
	"last_name": "Gates", 
	"summary": "Co-chair of the Bill & Melinda Gates... Active blogger.", 
	"region_id": "us:91", 
	"industry_id": 131,
	"photo_url": "/p/7/000/253/05b/308dd6e.jpg", 
	"positions": [ 
		{"job_title": "Co-chair", 
		"organization": "Bill & Melinda Gates Foundation"}, 
		{"job_title": "Co-founder, Chairman", 
		"organization": "Microsoft"} ], 
	"education": [ 
		{"school_name": "Harvard University", 
		"start": 1973, 
		"end": 1975}, 
		{"school_name": "Lakeside School, Seattle", 
		"start": null, 
		"end": null} 30 | Chapter 2: Data Models and Query Languages ], 
	"contact_info": 
	{ "blog": "http://thegatesnotes.com", 
	"twitter": "http://twitter.com/BillGates" } }
```
![[pic_tree_linkedin.png]]
- The above three examples show a difference in the storage of a LinkedIn profile between SQL, JSON, and a tree structure.
## 6. Related Concepts

- [[ ]]


---

## 7. Summary
The obect-relational mismatch is the mismatch between the storage layer and application code.