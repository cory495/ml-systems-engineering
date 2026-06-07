# Performance

Date: 2026-06-05

---

## 1. Definition
---
Performance is typically described by throughput (the total time to run a job on a dataset of a certain size) or response time (the total time between the client's request and the response received).
## 2. Why It Matters

---
Performance matters because it helps analyze load on increasing scales.
## 3. Key Ideas

---
- Both outliers an averages are important.
![[pic_outlier_example.png]]
## 4. Examples

---
- Service level objectives and service level agreements both define expected performance and availability.
## 5. How It Is Achieved

---
Typically load is used by analyzing a distribution of values and observing outliers and averages. Outliers are important when the clientele using them are of high value. Averages are important when the clientele are on average giving the same level of value. Large companies like Amazon pay special attention to both outliers and averages.
## 6. Tradeoffs

---
- Higher performance typically implies higher cost.
## 7. Related Concepts

- [[ Scalability]]
- [[Load]]

---

## 8. Summary
Performance is the measure of the successfulness of meeting certain goals in regards to the execution of tasks.