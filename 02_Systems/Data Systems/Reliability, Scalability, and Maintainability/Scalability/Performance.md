# Performance

Date: 2026-06-05

---

## 1. Definition

Performance describes how efficiently a system processes work under a given load.

The two most common performance metrics are:

- **Latency (Response Time)** — the time between a request being made and a response being received.
    
- **Throughput** — the amount of work completed per unit of time.
    

Performance helps engineers determine whether a system can meet user expectations as demand increases.

---

## 2. Why It Matters

Performance directly affects user experience and system capacity.

Poor performance can lead to:

- Slow applications
    
- Increased infrastructure costs
    
- Reduced user satisfaction
    
- System bottlenecks
    

Understanding performance allows engineers to identify limitations and improve system behavior under load.

---

## 3. Key Ideas

### Latency

Latency measures how long a single operation takes.

Examples:

- API response time
    
- Database query time
    
- Web page load time
    

Lower latency generally results in a better user experience.

### Throughput

Throughput measures how much work a system completes over time.

Examples:

- Requests per second
    
- Transactions per minute
    
- Files processed per hour
    

Higher throughput allows a system to support more users and workloads.

### Averages vs. Percentiles

Averages provide a general view of performance but can hide important outliers.

![[pic_outlier_example.png]]

Engineers often analyze:

- Average latency
    
- Median (P50)
    
- P95 latency
    
- P99 latency
    

Percentiles reveal the experience of slower users and help identify performance issues that averages may miss.

### Bottlenecks

A bottleneck is the component that limits overall system performance.

Common bottlenecks include:

- CPU
    
- Memory
    
- Storage
    
- Network bandwidth
    
- Database queries
    

Improving the bottleneck often provides the largest performance gains.

---

## 4. Examples

### Web Services

A web service may target:

- Average latency < 100 ms
    
- P99 latency < 500 ms
    

### Databases

Database performance is often measured using:

- Query latency
    
- Transactions per second (TPS)
    

### Service-Level Objectives

Organizations frequently define expected performance using:

- Service-Level Objectives (SLOs)
    
- Service-Level Agreements (SLAs)
    

These establish measurable targets for latency, throughput, and availability.

---

## 5. How It Is Measured

Performance is typically measured by:

- Benchmarking
    
- Load testing
    
- Stress testing
    
- Monitoring production systems
    

Engineers analyze distributions of latency and throughput rather than relying solely on averages.

Particular attention is often given to P95 and P99 latency because a small percentage of slow requests can significantly impact user experience.

---

## 6. Tradeoffs

Improving performance often increases:

- Infrastructure cost
    
- Engineering complexity
    
- Resource consumption
    

Examples:

- More servers increase throughput but cost more.
    
- Additional caching improves latency but adds operational complexity.
    
- Replication improves read performance but may increase consistency challenges.
    

---

## 7. Related Concepts

up:: [[Scalability]]

down:: [[Latency]]  
down:: [[Throughput]]

[[Load]]  
[[Reliability]]  
[[Caching]]  
[[Load Balancing]]  
[[Bottlenecks]]  
[[SLO]]  
[[SLA]]

---

## 8. Common Interview Questions

- What is the difference between latency and throughput?
    
- Why are percentiles often more useful than averages?
    
- What is P99 latency?
    
- How do you identify a bottleneck?
    
- How does load affect performance?
    
- What metrics would you monitor for a production service?
    

---

## 9. Summary

Performance measures how efficiently a system processes work under a given load. The primary metrics are latency and throughput. Engineers analyze averages, percentiles, and bottlenecks to understand system behavior and ensure applications meet performance goals as demand grows.