# Backend Interview Cheat Sheet

A comprehensive guide covering essential backend development concepts for technical interviews - from fundamental networking concepts to advanced distributed systems topics like CAP theorem and event-driven architecture.

## Table of Contents

1. [Internet & Networking Fundamentals](#internet--networking-fundamentals)
2. [HTTP & Web Protocols](#http--web-protocols)
3. [Database Concepts](#database-concepts)
4. [System Design Fundamentals](#system-design-fundamentals)
5. [Data Structures & Algorithms](#data-structures--algorithms)
6. [Security Concepts](#security-concepts)
7. [Performance & Scalability](#performance--scalability)
8. [DevOps & Deployment](#devops--deployment)
9. [Advanced Topics](#advanced-topics)
10. [Common Interview Questions](#common-interview-questions)

---

## Internet & Networking Fundamentals

### How the Internet Works
- **DNS (Domain Name System)**: Translates domain names to IP addresses
- **TCP/IP Protocol Stack**: Application → Transport → Internet → Network Access
- **OSI Model**: 7 layers (Physical, Data Link, Network, Transport, Session, Presentation, Application)
- **IP Addressing**: IPv4 (32-bit) vs IPv6 (128-bit)
- **Subnetting**: Dividing networks into smaller subnetworks

### Network Protocols
- **TCP**: Reliable, connection-oriented, ordered delivery
- **UDP**: Unreliable, connectionless, faster transmission
- **HTTP/HTTPS**: Application layer protocols for web communication
- **WebSockets**: Full-duplex communication over TCP
- **gRPC**: High-performance RPC framework using HTTP/2

### Load Balancing
- **Round Robin**: Distribute requests evenly across servers
- **Weighted Round Robin**: Assign different weights to servers
- **Least Connections**: Route to server with fewest active connections
- **IP Hash**: Route based on client IP hash
- **Health Checks**: Monitor server availability

---

## HTTP & Web Protocols

### HTTP Methods
- **GET**: Retrieve data (idempotent, cacheable)
- **POST**: Create new resources (not idempotent)
- **PUT**: Update/replace entire resource (idempotent)
- **PATCH**: Partial update (not necessarily idempotent)
- **DELETE**: Remove resource (idempotent)
- **HEAD**: Get headers only
- **OPTIONS**: Get allowed methods

### HTTP Status Codes
- **2xx Success**: 200 OK, 201 Created, 204 No Content
- **3xx Redirection**: 301 Moved Permanently, 302 Found, 304 Not Modified
- **4xx Client Error**: 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found
- **5xx Server Error**: 500 Internal Server Error, 502 Bad Gateway, 503 Service Unavailable

### HTTP Headers
- **Request Headers**: Authorization, Accept, User-Agent, Cookie
- **Response Headers**: Content-Type, Set-Cookie, Cache-Control, ETag
- **CORS Headers**: Access-Control-Allow-Origin, Access-Control-Allow-Methods

### RESTful API Design
- **Resource-based URLs**: `/users/123` instead of `/getUser?id=123`
- **HTTP methods map to CRUD operations**
- **Stateless**: Each request contains all necessary information
- **HATEOAS**: Hypermedia as the Engine of Application State
- **Versioning**: URL path (`/v1/users`) or headers (`Accept: application/vnd.api+json;version=1`)

---

## Database Concepts

### SQL Databases (RDBMS)
#### ACID Properties
- **Atomicity**: All operations in transaction succeed or fail together
- **Consistency**: Database remains in valid state
- **Isolation**: Concurrent transactions don't interfere
- **Durability**: Committed changes persist

#### Normalization
- **1NF**: Atomic values, no repeating groups
- **2NF**: 1NF + no partial dependencies on composite primary key
- **3NF**: 2NF + no transitive dependencies
- **BCNF**: 3NF + every determinant is candidate key

#### Indexing
- **Clustered Index**: Physical ordering of data
- **Non-clustered Index**: Separate structure pointing to data
- **Composite Index**: Multiple columns
- **Unique Index**: Ensures uniqueness
- **Partial Index**: Only subset of rows

#### Joins
- **INNER JOIN**: Only matching records
- **LEFT/RIGHT JOIN**: All records from one table + matching from other
- **FULL OUTER JOIN**: All records from both tables
- **CROSS JOIN**: Cartesian product

### NoSQL Databases
#### Types
- **Document**: MongoDB, CouchDB (JSON-like documents)
- **Key-Value**: Redis, DynamoDB (simple key-value pairs)
- **Column-Family**: Cassandra, HBase (wide columns)
- **Graph**: Neo4j, Amazon Neptune (nodes and relationships)

#### CAP Theorem
- **Consistency**: All nodes see same data simultaneously
- **Availability**: System remains operational
- **Partition Tolerance**: System continues despite network failures
- **Trade-off**: Can only guarantee 2 of 3 properties

### Database Patterns
- **Sharding**: Horizontal partitioning across multiple databases
- **Replication**: Master-slave, master-master configurations
- **Connection Pooling**: Reuse database connections
- **Read Replicas**: Separate read and write operations
- **Data Warehousing**: OLAP vs OLTP systems

---

## System Design Fundamentals

### Scalability Patterns
#### Horizontal vs Vertical Scaling
- **Vertical (Scale Up)**: Add more power to existing machine
- **Horizontal (Scale Out)**: Add more machines to pool of resources

#### Caching Strategies
- **Cache-Aside**: Application manages cache
- **Write-Through**: Write to cache and database simultaneously
- **Write-Behind**: Write to cache immediately, database later
- **Read-Through**: Cache loads data on miss
- **Cache Levels**: Browser → CDN → Reverse Proxy → Application → Database

#### Database Scaling
- **Read Replicas**: Distribute read operations
- **Database Sharding**: Partition data across multiple databases
- **Federation**: Split databases by function
- **Denormalization**: Trade storage for query performance

### System Architecture Patterns
#### Microservices vs Monolith
- **Monolith**: Single deployable unit, easier development/testing
- **Microservices**: Independent services, better scalability/technology diversity
- **Service Mesh**: Infrastructure layer for service-to-service communication

#### Message Queues
- **Synchronous**: Direct request-response (REST APIs)
- **Asynchronous**: Message queues (RabbitMQ, Apache Kafka, AWS SQS)
- **Pub/Sub**: Publishers send messages to topics, subscribers receive
- **Point-to-Point**: Direct message from producer to consumer

#### API Gateway
- **Single entry point** for all client requests
- **Cross-cutting concerns**: Authentication, rate limiting, logging
- **Service composition**: Aggregate multiple backend services
- **Protocol translation**: HTTP to gRPC, etc.

---

## Data Structures & Algorithms

### Time & Space Complexity
- **Big O Notation**: O(1), O(log n), O(n), O(n log n), O(n²), O(2ⁿ)
- **Best, Average, Worst Case** analysis
- **Space-time trade-offs**

### Essential Data Structures
#### Arrays & Strings
- **Dynamic Arrays**: Resizing, amortized O(1) insertion
- **String manipulation**: Pattern matching, parsing

#### Hash Tables
- **Hash Functions**: Distribute keys uniformly
- **Collision Resolution**: Chaining vs Open Addressing
- **Load Factor**: Impact on performance

#### Trees
- **Binary Search Trees**: O(log n) search, insert, delete
- **Balanced Trees**: AVL, Red-Black trees
- **B-Trees**: Database indexing, disk-based storage
- **Trie**: Prefix trees for string searching

#### Graphs
- **Representation**: Adjacency matrix vs adjacency list
- **Traversal**: BFS (shortest path), DFS (connectivity)
- **Shortest Path**: Dijkstra's, Bellman-Ford algorithms

### Common Algorithms
- **Sorting**: QuickSort O(n log n), MergeSort O(n log n), HeapSort O(n log n)
- **Searching**: Binary Search O(log n), Linear Search O(n)
- **Graph Algorithms**: Topological Sort, Minimum Spanning Tree
- **Dynamic Programming**: Memoization, optimal substructure

---

## Security Concepts

### Authentication & Authorization
#### Authentication Methods
- **Username/Password**: Basic authentication
- **Multi-Factor Authentication (MFA)**: Something you know/have/are
- **OAuth 2.0**: Authorization framework for third-party access
- **JWT (JSON Web Tokens)**: Stateless authentication tokens
- **SAML**: XML-based authentication standard

#### Authorization Patterns
- **Role-Based Access Control (RBAC)**: Users assigned to roles
- **Attribute-Based Access Control (ABAC)**: Dynamic permissions based on attributes
- **Access Control Lists (ACL)**: User-specific permissions per resource

### Web Security
#### Common Vulnerabilities
- **SQL Injection**: Malicious SQL code execution
- **Cross-Site Scripting (XSS)**: Client-side script injection
- **Cross-Site Request Forgery (CSRF)**: Unauthorized actions on behalf of user
- **Man-in-the-Middle**: Intercepting communication
- **DDoS**: Distributed Denial of Service attacks

#### Security Headers
- **Content-Security-Policy (CSP)**: Prevent XSS attacks
- **X-Frame-Options**: Prevent clickjacking
- **Strict-Transport-Security (HSTS)**: Force HTTPS
- **X-Content-Type-Options**: Prevent MIME sniffing

### Cryptography
- **Symmetric**: Same key for encryption/decryption (AES)
- **Asymmetric**: Public/private key pairs (RSA, ECC)
- **Hashing**: One-way functions (SHA-256, bcrypt for passwords)
- **Digital Signatures**: Verify authenticity and integrity
- **TLS/SSL**: Secure communication protocols

---

## Performance & Scalability

### Performance Optimization
#### Database Optimization
- **Query Optimization**: Proper indexing, query analysis
- **Connection Pooling**: Reuse database connections
- **Database Sharding**: Distribute data across multiple databases
- **Caching**: Redis, Memcached for frequently accessed data

#### Application Performance
- **Profiling**: Identify bottlenecks in code
- **Lazy Loading**: Load data only when needed
- **Pagination**: Limit result sets
- **Compression**: Reduce payload size (gzip, Brotli)
- **CDN**: Content Delivery Networks for static assets

### Monitoring & Observability
#### Key Metrics
- **Latency**: Response time for requests
- **Throughput**: Requests per second
- **Error Rate**: Percentage of failed requests
- **Resource Utilization**: CPU, memory, disk usage

#### Monitoring Tools
- **APM**: Application Performance Monitoring (New Relic, DataDog)
- **Logging**: Structured logging, log aggregation (ELK stack)
- **Tracing**: Distributed tracing (Jaeger, Zipkin)
- **Metrics**: Time-series data (Prometheus, Grafana)

---

## DevOps & Deployment

### Containerization
#### Docker
- **Images**: Read-only templates for containers
- **Containers**: Running instances of images
- **Dockerfile**: Instructions to build images
- **Multi-stage builds**: Optimize image size
- **Volume mounting**: Persist data outside containers

#### Orchestration
- **Kubernetes**: Container orchestration platform
- **Pods**: Smallest deployable units
- **Services**: Stable endpoints for pods
- **ConfigMaps/Secrets**: Configuration management
- **Ingress**: External access to services

### CI/CD Pipelines
#### Continuous Integration
- **Version Control**: Git workflows (feature branches, pull requests)
- **Automated Testing**: Unit, integration, end-to-end tests
- **Code Quality**: Linting, static analysis, code coverage
- **Build Automation**: Compile, package, create artifacts

#### Continuous Deployment
- **Deployment Strategies**: Blue-green, rolling updates, canary releases
- **Infrastructure as Code**: Terraform, CloudFormation
- **Configuration Management**: Ansible, Chef, Puppet
- **Monitoring**: Health checks, rollback procedures

### Cloud Services
#### Common Patterns
- **Serverless**: AWS Lambda, Google Cloud Functions
- **Message Queues**: AWS SQS, Google Pub/Sub
- **Object Storage**: AWS S3, Google Cloud Storage
- **Managed Databases**: AWS RDS, Google Cloud SQL
- **Auto Scaling**: Dynamic resource allocation

---

## Advanced Topics

### Event-Driven Architecture
#### Event Sourcing
- **Event Store**: Immutable log of events
- **Event Replay**: Rebuild state from events
- **Snapshots**: Periodic state checkpoints
- **CQRS**: Command Query Responsibility Segregation

#### Message Patterns
- **Event Notification**: Simple event announcements
- **Event-Carried State Transfer**: Events contain full state
- **Event Sourcing**: Events as source of truth
- **Saga Pattern**: Manage distributed transactions

### Consistency Models
#### Strong Consistency
- **Linearizability**: Operations appear instantaneous
- **Sequential Consistency**: Program order preserved
- **ACID Transactions**: Database consistency guarantees

#### Eventual Consistency
- **BASE**: Basically Available, Soft state, Eventual consistency
- **Vector Clocks**: Track causality in distributed systems
- **Conflict Resolution**: Last-writer-wins, application-specific

### Distributed Systems Patterns
#### Consensus Algorithms
- **Raft**: Leader-based consensus
- **Paxos**: Byzantine fault-tolerant consensus
- **PBFT**: Practical Byzantine Fault Tolerance

#### Circuit Breaker Pattern
- **Closed**: Normal operation
- **Open**: Failing fast, preventing cascade failures
- **Half-Open**: Testing if service recovered

#### Bulkhead Pattern
- **Isolation**: Separate resource pools
- **Failure Containment**: Prevent total system failure

---

## Common Interview Questions

### System Design Questions
1. **Design a URL shortener (like bit.ly)**
   - Database schema, URL encoding, caching strategy
   
2. **Design a chat system**
   - WebSockets, message queues, user presence, scaling

3. **Design a social media feed**
   - Timeline generation, fan-out strategies, caching

4. **Design a ride-sharing service**
   - Geospatial indexing, matching algorithms, real-time updates

5. **Design a distributed cache**
   - Consistent hashing, replication, cache coherence

### Technical Questions
1. **Explain the difference between SQL and NoSQL databases**
2. **What is the CAP theorem and how does it apply?**
3. **How would you handle a million concurrent users?**
4. **Explain different types of caching and when to use each**
5. **What are microservices and their trade-offs vs monoliths?**
6. **How do you ensure data consistency in distributed systems?**
7. **Explain OAuth 2.0 flow and JWT tokens**
8. **What are different HTTP status codes and their meanings?**
9. **How would you optimize a slow database query?**
10. **Explain the difference between horizontal and vertical scaling**

### Coding Questions
- **String manipulation**: Reverse, palindrome, anagrams
- **Array problems**: Two pointers, sliding window, binary search
- **Tree traversals**: In-order, pre-order, post-order, level-order
- **Graph algorithms**: BFS, DFS, shortest path
- **Dynamic programming**: Memoization, bottom-up approaches
- **System design coding**: Rate limiter, LRU cache implementation

---

## Quick Reference

### HTTP Status Codes
- **200**: OK
- **201**: Created
- **400**: Bad Request
- **401**: Unauthorized
- **403**: Forbidden
- **404**: Not Found
- **500**: Internal Server Error

### Time Complexities
- **O(1)**: Hash table lookup
- **O(log n)**: Binary search, balanced tree operations
- **O(n)**: Linear search, single loop
- **O(n log n)**: Efficient sorting algorithms
- **O(n²)**: Nested loops, bubble sort

### Database Normalization
- **1NF**: Atomic values
- **2NF**: No partial dependencies
- **3NF**: No transitive dependencies
- **BCNF**: Every determinant is candidate key

This cheat sheet provides a comprehensive overview of backend development concepts commonly covered in technical interviews. Use it as a reference guide to review key topics and prepare for system design discussions.
