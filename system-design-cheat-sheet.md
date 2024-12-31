# System Design Cheat Sheet

## Overview
System design is the process of designing the architecture of an entire system, including hardware, software, data storage, and networking components. A solid understanding of system design is essential for building scalable, efficient, and fault-tolerant systems.

This cheat sheet provides a high-level overview of the most important concepts in system design, and it’s aimed at helping you prepare for system design interviews or work on large-scale distributed systems.

## Table of Contents
1. [System Design Basics](#system-design-basics)
2. [Key Principles](#key-principles)
3. [Core System Components](#core-system-components)
4. [Design Patterns](#design-patterns)
5. [Scalability Considerations](#scalability-considerations)
6. [Performance Optimization](#performance-optimization)
7. [High Availability and Fault Tolerance](#high-availability-and-fault-tolerance)
8. [Data Storage and Caching](#data-storage-and-caching)
9. [Network and Communication](#network-and-communication)
10. [Security Considerations](#security-considerations)
11. [Monitoring and Maintenance](#monitoring-and-maintenance)
12. [Examples and Case Studies](#examples-and-case-studies)

---

## System Design Basics

### 1. **Understand the Requirements**
   - **Functional Requirements**: What does the system need to do? Example: An e-commerce website must support user registration, search, orders, etc.
   - **Non-Functional Requirements**: How should the system perform? Example: scalability, availability, latency, throughput, fault tolerance.

### 2. **Identify Constraints**
   - Time, budget, technical constraints.
   - Consider limits in terms of scalability, data capacity, and performance.

### 3. **Define the High-Level Architecture**
   - Identify key components (front-end, back-end, database, etc.)
   - Define communication between components (API calls, message queues, etc.)

---

## Key Principles

### 1. **Scalability**
   - **Vertical Scaling**: Increasing capacity of a single machine (CPU, RAM).
   - **Horizontal Scaling**: Adding more machines to distribute the load (load balancing).
   - **Load Balancing**: Distributing requests across multiple servers to ensure even load distribution.

### 2. **Availability**
   - **High Availability (HA)**: The system should be designed so that it remains operational despite failures.
   - **Redundancy**: Replicating critical components (e.g., databases, servers) to ensure service availability.
   
### 3. **Consistency**
   - **ACID**: Atomicity, Consistency, Isolation, Durability (for relational databases).
   - **CAP Theorem**: Consistency, Availability, Partition Tolerance (can only guarantee two of these three).

### 4. **Fault Tolerance**
   - **Graceful Degradation**: The system should continue to function, even if some components fail.
   - **Circuit Breakers**: Protecting the system from repeated failures by cutting off failing services.

---

## Core System Components

### 1. **Databases**
   - **Relational Databases (SQL)**: Data is stored in tables and relationships are defined between tables. Examples: MySQL, PostgreSQL.
   - **NoSQL Databases**: Non-tabular data storage, often schema-less. Examples: MongoDB, Cassandra.
   - **Data Warehouses**: Optimized for reporting and analytics. Examples: Google BigQuery, Amazon Redshift.
   - **NewSQL**: Combines the benefits of SQL and NoSQL. Example: Google Spanner.

### 2. **Caching**
   - **In-Memory Caches**: Store data in memory for fast access. Examples: Redis, Memcached.
   - **Content Delivery Networks (CDN)**: Cache static assets closer to users. Example: Cloudflare, Akamai.

### 3. **Message Queues**
   - **Asynchronous Communication**: Decouple services by sending messages. Examples: Kafka, RabbitMQ.
   - **Event-Driven Architecture**: Systems that react to events and messages rather than synchronous requests.

### 4. **APIs**
   - **REST**: Representational State Transfer (HTTP-based APIs).
   - **GraphQL**: Query language for APIs.
   - **gRPC**: Remote procedure calls (binary protocol) often used in microservices.

### 5. **Microservices**
   - Decompose the system into smaller, loosely coupled services.
   - **API Gateway**: A single entry point for multiple microservices.

---

## Design Patterns

### 1. **Client-Server Model**
   - The client makes requests to the server which processes and responds.

### 2. **Layered Architecture**
   - Organize the system into layers (presentation, business logic, data access) for better separation of concerns.

### 3. **Event-Driven Architecture**
   - Events trigger actions in other services. It’s often used with message queues.

### 4. **CQRS (Command Query Responsibility Segregation)**
   - Separate the command (write) and query (read) operations to optimize performance.

---

## Scalability Considerations

### 1. **Sharding**
   - Splitting a large database into smaller, more manageable pieces (shards) to scale horizontally.
   
### 2. **Partitioning**
   - Data is split and distributed across multiple nodes or databases.

### 3. **Load Balancing**
   - Techniques like round-robin, least connections, or IP hash are used to distribute traffic across servers.

### 4. **Global Distribution**
   - Use multiple data centers across different regions to improve scalability and reduce latency.

---

## Performance Optimization

### 1. **Database Indexing**
   - Use indexes to speed up data retrieval.
   
### 2. **Query Optimization**
   - Optimize database queries by reducing joins, filtering early, and using proper indexes.

### 3. **Content Compression**
   - Compress data, such as images and JSON payloads, to save bandwidth and speed up response times.

### 4. **Lazy Loading**
   - Load resources or data only when necessary to save on processing time.

---

## High Availability and Fault Tolerance

### 1. **Replication**
   - **Master-Slave Replication**: Primary database handles writes, while replicas handle reads.
   - **Multi-Region Replication**: Ensures availability and low latency across different geographical regions.

### 2. **Failover Systems**
   - Automatic switching to a backup system in case the primary system fails.

### 3. **Backups**
   - Regular backups to ensure data integrity and recovery in case of failure.

---

## Data Storage and Caching

### 1. **Databases**
   - Use different types of databases depending on your use case. SQL for structured data, NoSQL for unstructured data.

### 2. **CDN for Static Assets**
   - Distribute static files (images, scripts) across a CDN for faster delivery.

### 3. **Cache Invalidation**
   - Set proper cache expiration times, and use strategies like TTL (Time to Live) or versioning to ensure fresh content.

---

## Network and Communication

### 1. **API Rate Limiting**
   - Protect your system by limiting the number of requests a user can make within a certain period.

### 2. **Service Discovery**
   - Allows microservices to find and communicate with each other, often using tools like Consul or Eureka.

### 3. **Protocol Buffers vs JSON**
   - Protocol Buffers are faster and more efficient than JSON, but JSON is more human-readable.

### 4. **TLS/SSL Encryption**
   - Use HTTPS to secure communication between clients and servers.

---

## Security Considerations

### 1. **Authentication and Authorization**
   - **OAuth**: Standard for access delegation.
   - **JWT (JSON Web Tokens)**: Used for securely transmitting information between parties.

### 2. **Data Encryption**
   - Encrypt sensitive data both in transit (using TLS) and at rest (using AES or RSA).

### 3. **Input Validation**
   - Always sanitize user input to avoid SQL injection, XSS, and other vulnerabilities.

---

## Monitoring and Maintenance

### 1. **Logging**
   - Log errors, requests, and other important metrics for debugging and monitoring.
   - Use centralized logging tools like ELK Stack (Elasticsearch, Logstash, Kibana) or Splunk.

### 2. **Monitoring**
   - Use monitoring tools like Prometheus, Grafana, or Datadog to track system health and performance.

### 3. **Alerting**
   - Set up alerts to notify the team when the system is underperforming or has critical issues.

---

## Examples and Case Studies

### 1. **Designing a URL Shortener (like bit.ly)**
   - **Functional Requirements**: Shorten a URL and redirect to the original URL.
   - **Non-Functional Requirements**: High availability, low latency.
   - **Key Considerations**: Hashing algorithm, database choice, caching frequently used URLs.

### 2. **Designing an Online Bookstore**
   - **Functional Requirements**: Users can browse, purchase, and review books.
   - **Non-Functional Requirements**: Scalability, security, and high availability.
   - **Key Considerations**: Payment gateways, inventory management, user authentication.

---

## Conclusion
System design is a vast and nuanced field, and this cheat sheet serves as a starting point for diving into core concepts. Whether you are designing a simple application or a complex distributed system, these principles, patterns, and practices will help guide your decisions toward building efficient, scalable, and reliable systems.

For more in-depth information, it's recommended to study real-world case studies and experiment with system design challenges regularly.
