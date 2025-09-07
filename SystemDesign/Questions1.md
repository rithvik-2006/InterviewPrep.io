

# 📝 System Design Interview Question Bank

## 1. Introduction to System Design

* What do we mean by *system design*? How is it different from coding?
* How would you design a system to scale from 100 users to 10M users?
* What is the tradeoff between building a “perfect” design vs iterating quickly?

---

## 2. Computer Architecture Basics

* Explain the difference between **HDD, SSD, RAM, and Cache** in terms of speed and persistence.
* Why do CPUs need **caches (L1, L2, L3)** if we already have RAM?
* What happens in the system when you run a program written in Python?
* Compare volatile and non-volatile memory with examples.

---

## 3. High-Level Architecture of a Production-Ready App

* What is a **CI/CD pipeline**? Why is automation important?
* Explain the difference between a **load balancer** and a **reverse proxy**.
* How would you design a **logging and monitoring system** for a production app?
* Why should debugging never be done directly in production?

---

## 4. Pillars of System Design

* Define **Scalability, Maintainability, Efficiency, and Fault Tolerance** with real-world examples.
* What are the three main elements of system design: **moving, storing, transforming data**? Give an example of each.
* If a system is prone to failures, what design principles should you apply?

---

## 5. CAP Theorem

* State the **CAP theorem**.
* Why can’t we have **Consistency, Availability, and Partition Tolerance** all at once?
* Which CAP properties would you choose for:

  * A banking app
  * A social media feed
* Give an example of when **availability** is more important than **consistency**.

---

## 6. System Measurement & Resilience

* What does **99.999% availability** mean in terms of downtime per year?
* Differentiate between **SLO** and **SLA**.
* What is **graceful degradation**? Give an example.
* Define **throughput** vs **latency**. Can you optimize both simultaneously?
* How do you design a system for **fault tolerance**?

---

## 7. Networking Basics

* Difference between **IPv4 and IPv6**? Why do we need IPv6?
* Explain **TCP vs UDP**. When would you use UDP over TCP?
* What is the role of **DNS** in the internet?
* What happens when you type `google.com` in your browser?
* What is the purpose of **ports** in networking?

---

## 8. Application Layer Protocols

* Compare **HTTP vs WebSockets**.
* What do HTTP status codes `200`, `301`, `404`, `500` mean?
* Difference between **IMAP, POP3, SMTP**?
* What is **gRPC** and how is it different from **REST**?
* When would you use **MQTT** or **AMQP**?

---

## 9. API Design

* Explain **CRUD operations** with HTTP methods.
* What is the main drawback of **REST** that **GraphQL** solves?
* Explain **idempotency** with an example.
* How do you design APIs to be **backward compatible**?
* Why is **rate limiting** important in API design?

---

## 10. Caching and CDNs

* Difference between **cache hit** and **cache miss**?
* Compare **Write-through, Write-around, and Write-back cache** strategies.
* What are **LRU, LFU, FIFO** eviction policies?
* Explain the difference between **browser caching, server caching, and database caching**.
* When would you use a **CDN** and when would you avoid it?

---

## 11. Proxy Servers

* Difference between **forward proxy** and **reverse proxy**.
* How do **CDNs** act as reverse proxies?
* What is an **open proxy**? Why is it dangerous?
* What is **SSL offloading** and why would you do it at a proxy?

---

## 12. Load Balancers

* Difference between **Round Robin** and **Least Connections** load balancing.
* What is **IP Hashing** and when is it useful?
* How would you prevent a **load balancer from becoming a single point of failure**?
* Difference between **software, hardware, and cloud load balancers**.
* What is a **health check** in load balancing?

---

## 13. Databases

* Difference between **SQL vs NoSQL** databases.
* Explain **ACID properties** with examples.
* What is **sharding**? Explain **range-based vs directory-based sharding**.
* Difference between **master-slave** and **master-master replication**.
* When would you use an **in-memory database** like Redis?
* How does **indexing** improve performance in SQL databases?


