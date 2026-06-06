# Faults

Date: 2026-06-05

---
## 1. Definition

---
Things that can go wrong. A fault is not a failure. A fault is a component of the system deviating from the spec, but a failure is when a system as a whole stops.
![[draw_fault_failure]]
## 2. Why It Matters

---
Faults are impossible to reduce to zero. Thus, faults are important to acknowledge, so that fault-tolerant systems can be created. In this way, systems can be created that prevent faults from causing failures.
## 3. Key Ideas

---
- Creating fault-tolerant systems is more important and doable than reducing faults to zero.
![[draw_fault_types]]
## 4. Examples

---
- The preventable AWS failure caused from a fault when updating the software could have been easily prevented if procedures for developers were more rigorously applied.
## 5. How It Is Achieved

---
- Creating fault-tolerant systems is achieved through many different procedures, tools, and systems all put together.
## 6. Tradeoffs

---
- Preventing faults typically have some cost related to them. This can be from employing more humans to utilizing more hardware.
## 7. Related Concepts

- [[Hardware Faults ]]
- [[Software Errors]]
- [[Human Errors]]
- 
---
## 8. Summary
Faults are errors caused by hardware, software, or humans that mess up one component of a data system. Faults are not the same thing as failures.