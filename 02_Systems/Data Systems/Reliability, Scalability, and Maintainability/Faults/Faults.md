# Faults

Date: 2026-06-05

---

## 1. Definition

A fault is a defect or abnormal condition in a system component that deviates from its expected behavior.

A fault does not necessarily cause a system-wide problem.

A **failure** occurs when a fault leads to the system (or a service) being unable to provide correct service.

> Fault ≠ Failure  
> Fault -> potential problem  
> Failure -> observable incorrect system behavior

![[draw_fault_failure]]

---

## 2. Why It Matters

Faults are unavoidable in real-world systems.

They occur due to:

- Hardware degradation
    
- Software bugs
    
- Human mistakes
    
- Environmental conditions
    

Because faults cannot be eliminated entirely, system design focuses on ensuring that faults do not escalate into failures.

This leads to the concept of **fault tolerance**: designing systems that continue functioning correctly even when components fail.

---

## 3. Key Ideas

### Faults are inevitable

At scale, some component will always be failing.

### Failure is system-level

A failure is what users observe when the system stops working correctly.

### Fault tolerance is the goal

Instead of preventing all faults, systems aim to:

- Detect faults
    
- Isolate faults
    
- Recover from faults
    
- Contain faults so they do not spread
    

![[draw_fault_types]]

### Fault types

- [[Hardware Faults]] — physical component failures
    
- [[Software Errors]] — bugs and logic failures
    
- [[Human Errors]] — operational mistakes
    

---

## 4. Examples

### Software Deployment Fault

A misconfigured deployment introduces a bug that crashes a subset of service instances. The system may or may not fail depending on redundancy and recovery mechanisms.

---

### AWS-style Incident

A configuration or update error affects part of a distributed system. Whether it becomes a failure depends on whether redundancy, failover, and rollback mechanisms are in place.

---

### Disk Failure

A single disk fails in a replicated storage system. The system continues operating normally due to redundancy.

---

## 5. How It Is Addressed

Faults are handled through system design techniques such as:

- Replication
    
- Redundancy
    
- Failover systems
    
- Monitoring and alerting
    
- Circuit breakers
    
- Backpressure
    
- Automated recovery
    
- Graceful degradation
    

The goal is not to eliminate faults, but to prevent them from causing failures.

---

## 6. Tradeoffs

Improving fault tolerance typically increases:

- Infrastructure cost
    
- System complexity
    
- Operational overhead
    
- Latency (in some cases, due to redundancy or coordination)
    

However, these costs are justified in systems that require high availability and correctness.

---

## 7. Related Concepts

down:: [[Hardware Faults]]  
down:: [[Software Errors]]  
down:: [[Human Errors]]

[[Reliability]]  
[[Fault Tolerance]]  
[[Replication]]  
[[Redundancy]]  
[[Failure Detection]]

---

## 8. Common Interview Questions

- What is the difference between a fault and a failure?
    
- Why can’t faults be eliminated in large systems?
    
- What is fault tolerance?
    
- How do distributed systems handle faults?
    
- What techniques prevent faults from becoming failures?
    
- Why is redundancy important?
    

---

## 9. Summary

A fault is a defect or abnormal condition in a system component, while a failure is when that fault leads to incorrect system behavior. Because faults are unavoidable, system design focuses on fault tolerance—ensuring that faults do not become failures.