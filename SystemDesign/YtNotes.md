Here are detailed revision notes with examples for the system design concepts discussed:

### 1. Introduction to System Design

System design involves understanding how to **glue an entire system together**. It's a comprehensive crash course covering concepts like **scalability, reliability, data handling, and high-level architecture**. The focus is not on writing actual code but on the overall structure and interaction of components.

### 2. Computer Architecture Basics

Before designing large-scale distributed systems, it's crucial to understand the **high-level architecture of individual computers**. Computers operate through a layered system, each optimized for different tasks.

*   **Bits and Bytes**: At its core, a computer understands only **binary zeros and ones**, represented as **bits**. One bit is the smallest data unit. **One byte consists of eight bits** and can represent a single character or number. Larger units include kilobyte, megabyte, gigabyte, and terabyte.
*   **Disk Storage**:
    *   **Non-volatile** storage that retains data even without power.
    *   Stores the **OS, applications, and all user files**.
    *   Can be **HDD (Hard Disk Drive)** or **SSD (Solid State Drive)**.
    *   **HDDs** typically offer read speeds of 80-160 MB/s, while **SSDs** are significantly faster, ranging from 500 MB/s to 3,500 MB/s, but are more expensive.
    *   Sizes typically range from hundreds of gigabytes to multiple terabytes.
*   **RAM (Random Access Memory)**:
    *   The **primary active data holder**.
    *   Stores data structures, variables, and application data currently in use.
    *   **Volatile memory**: requires power to retain contents, data is not persisted after a restart.
    *   Offers **quick read and write access**.
    *   Read/write speeds often surpass 5,000 MB/s, faster than even the fastest SSDs.
    *   Sizes range from a few gigabytes in consumer devices to hundreds of gigabytes in high-end servers.
*   **Cache**:
    *   Smaller than RAM, typically measured in megabytes.
    *   **Access times are even faster than RAM**, offering just a few nanoseconds for L1 cache.
    *   **Purpose**: To **reduce the average time to access data** by storing frequently used data.
    *   **Hierarchy**: CPU first checks L1, then L2, L3, and finally RAM if data is not found.
*   **CPU (Central Processing Unit)**:
    *   The **"brain of the computer"**.
    *   **Fetches, decodes, and executes instructions**.
    *   Processes operations defined in your code.
    *   Code written in high-level languages (e.g., Java, C++, Python) must first be **compiled into machine code** by a compiler for the CPU to execute it.
    *   Can read and write from RAM, disk, and cache.
*   **Motherboard (Mainboard)**:
    *   Connects all components, providing **pathways for data flow**.

### 3. High-Level Architecture of a Production-Ready App

A production-ready application involves several key areas:

*   **CI/CD Pipeline (Continuous Integration and Continuous Deployment)**:
    *   Ensures code moves from repository, through tests and checks, to the production server **without manual intervention**.
    *   **Automates deployment processes** using platforms like Jenkins or GitHub Actions.
*   **Load Balancers and Reverse Proxies**:
    *   Managed by tools like **nginx**.
    *   **Evenly distribute user requests across multiple servers**.
    *   Maintain a smooth user experience even during traffic spikes.
*   **External Storage Server**:
    *   Stores data and is **not running on the same production server** but connected over a network.
*   **Logging and Monitoring Systems**:
    *   Keep an eye on every micro-interaction by **storing logs and analyzing data**.
    *   Logs are typically stored on external services, often outside the primary production server.
    *   **Backend tools**: pm2 for logging and monitoring.
    *   **Frontend platforms**: Sentry to capture and report errors in real-time.
*   **Alerting Service**:
    *   When logging systems detect failing requests or anomalies, they **notify an alerting service**.
    *   Push notifications are sent to users (e.g., "something went wrong," "payment failed").
    *   Modern practice integrates alerts directly into platforms like **Slack**, allowing developers to address issues instantly.
*   **Debugging Process**:
    *   **Identify the issue**: Developers use logs to search for patterns or anomalies.
    *   **Replicate in a safe environment**: Issues are recreated in a staging or test environment, never directly in production, to avoid affecting users.
    *   **Use debugging tools**: Developers use tools to peer into the running application.
    *   **Roll out a hotfix**: A quick, temporary fix is implemented to get things running again, acting as a patch before a permanent solution.

### 4. Pillars of System Design

A good system design focuses on several key principles and elements:

*   **Good Design Principles**:
    *   **Scalability**: The system's ability to **grow with its user base**.
    *   **Maintainability**: Ensuring future developers can **understand and improve the system**.
    *   **Efficiency**: **Making the best use of resources**.
    *   **Planning for Failure**: Building a system that performs well even when things go wrong and **maintains composure during failures**.
*   **Three Key Elements**:
    *   **Moving Data**: Ensuring data flows seamlessly, optimizing for speed and security (e.g., user requests to servers, data transfers between databases).
    *   **Storing Data**: Involves choosing databases (SQL/NoSQL), understanding access patterns, indexing strategies, and backup solutions to ensure data is secure and available.
    *   **Transforming Data**: Taking raw data and turning it into meaningful information (e.g., aggregating log files for analysis, converting user input).

### 5. CAP Theorem (Brewer's Theorem)

The **CAP theorem** guides tradeoffs in distributed systems, stating that a system can only achieve two out of three properties simultaneously.

*   **Consistency (C)**: All nodes in the distributed system have the **same data at the same time**. If one node changes, that change is reflected across all nodes.
    *   **Example**: Updating a Google Doc – everyone sees the edit immediately.
*   **Availability (A)**: The system is **always operational and responsive** to requests.
    *   **Example**: A reliable online store is always open and ready to take orders.
*   **Partition Tolerance (P)**: The system continues to function even when a **network partition** (disruption in communication between nodes) occurs.
    *   **Example**: A group chat where even if one person loses connection, the rest can continue chatting.

**Tradeoffs**:
*   Prioritizing **Consistency and Partition Tolerance** might compromise **Availability**.
    *   **Example**: A banking system needs consistency and partition tolerance for financial accuracy, even if transactions take longer, temporarily compromising availability.
*   Every design decision involves tradeoffs; it's about finding the **best solution for the specific use case**.

### 6. System Measurement & Resilience

*   **Availability**:
    *   Measures a system's **operational performance and reliability** – "Is our system up and running when our users need it?".
    *   Measured in **percentage**, often aiming for **"5 9's" (99.999%) availability**.
        *   **Example**: 99.9% availability allows 8.76 hours of downtime per year, while 99.999% allows only about 5 minutes of downtime per year.
    *   Measured in **uptime and downtime**.
    *   **SLOs (Service Level Objectives)**: **Goals** for system performance and availability.
        *   **Example**: Web service should respond within 300 milliseconds and 99.9% of the time.
    *   **SLAs (Service Level Agreements)**: **Formal contracts** with users/customers defining minimum service levels. If an SLA is not met (e.g., guaranteed 99.99% availability drops below), compensation might be required.
*   **Resilience**: Building resilience means **expecting the unexpected**.
    *   **Redundant systems**: Implementing backups ready to take over in case of failure.
    *   **Graceful degradation**: Designing the system so core functionality remains intact even if certain features are unavailable.
*   **Reliability**: Ensuring the system **works correctly and consistently**.
*   **Fault Tolerance**: Preparing for when things go wrong; how the system **handles unexpected failures or attacks**.
*   **Redundancy**: Having **backups** so if one part fails, another takes its place.
*   **Speed**:
    *   **Throughput**: Measures **how much data a system can handle over a period**.
        *   **Server Throughput**: Requests per second (RPS). Higher RPS indicates better performance.
        *   **Database Throughput**: Queries per second (QPS). Higher QPS signifies better performance.
        *   **Data Throughput**: Bytes per second (reflects data transferred over a network or processed).
    *   **Latency**: Measures **how long it takes to handle a single request** (time from request to response).
    *   **Tradeoff**: Optimizing for one (e.g., batching operations for throughput) can sacrifice the other (e.g., increasing latency).
    *   **Importance of good design**: Poor design leads to bottlenecks and vulnerabilities; redesigning is monumental, so getting it right from the start is crucial.

### 7. Networking Basics

*   **IP Address (Internet Protocol Address)**:
    *   A **unique identifier for each device on a network**.
    *   **IPv4**: 32-bit, allowing ~4 billion unique addresses.
    *   **IPv6**: 128-bit, significantly increasing available unique addresses due to the growing number of devices.
    *   **Public IP addresses**: Unique across the internet.
    *   **Private IP addresses**: Unique within a local network.
    *   Can be **static** (permanently assigned) or **dynamic** (changing over time, common for residential connections).
*   **Data Packets and Internet Protocol**:
    *   Computers send and receive **packets of data** over a network.
    *   Each packet contains an **IP header** with sender and receiver IP addresses.
    *   The **Internet Protocol** defines how data is sent and received.
*   **Application Layer**:
    *   Data specific to the application protocol (e.g., HTTP for web browsing) is stored here, formatted for correct interpretation.
*   **Transport Layer (TCP and UDP)**:
    *   **TCP (Transmission Control Protocol)**:
        *   **Reliable communication**.
        *   Ensures complete and correct delivery of data packets.
        *   Uses **sequence numbers** to track packet order.
        *   Establishes a stable connection via a **three-way handshake**.
        *   Each data packet includes a TCP header with port numbers and control flags.
    *   **UDP (User Datagram Protocol)**:
        *   **Faster but less reliable** than TCP.
        *   Doesn't establish a connection or guarantee delivery/order.
        *   Preferable for **time-sensitive communications** where speed is crucial and some data loss is acceptable (e.g., video calls, live streaming).
*   **DNS (Domain Name System)**:
    *   Acts like the **internet phone book**, translating **human-friendly domain names into IP addresses**.
    *   When you enter a URL, the browser sends a DNS query to find the IP address and connect to the server.
    *   **ICANN** oversees DNS, and registrars (e.g., Namecheap, GoDaddy) sell domain names.
    *   Uses **A records** (maps domain to IPv4) and **AAAA records** (maps domain to IPv6).
*   **Networking Infrastructure**:
    *   **Firewalls**: Monitor and control incoming/outgoing network traffic to protect networks.
    *   **Ports**: Identify specific processes or services within a device. Combined with an IP address, they form a unique identifier for a network service.
        *   **Example**: Port 80 for HTTP, Port 22 for SSH.

### 8. Application Layer Protocols

*   **HTTP (Hypertext Transfer Protocol)**:
    *   Built on TCP/IP.
    *   A **request-response protocol with no memory (stateless)**. Each interaction is separate; the server doesn't store context between requests.
    *   Requests include headers (URL, Method) and a body.
    *   Responses include a **status code** providing feedback.
        *   **200 series**: Success (e.g., 200 OK).
        *   **300 series**: Redirection (e.g., 301 Moved Permanently).
        *   **400 series**: Client error (e.g., 404 Not Found, 400 Bad Request).
        *   **500 series**: Server error (e.g., 500 Internal Server Error).
    *   **Common Methods**:
        *   **GET**: Fetching data.
        *   **POST**: Creating data on the server.
        *   **PUT/PATCH**: Updating a record.
        *   **DELETE**: Removing a record.
*   **WebSockets**:
    *   Provides a **two-way (bidirectional) communication channel** over a single, long-lived connection.
    *   Allows servers to push real-time updates to clients.
    *   Important for applications requiring constant data updates without repeated HTTP request/response cycles.
    *   **Examples**: Chat applications, live sport updates, stock market feeds.
*   **Email Protocols**:
    *   **SMTP (Simple Mail Transfer Protocol)**: Standard for **sending email messages** between servers. Most email clients use it for sending.
    *   **IMAP (Internet Message Access Protocol)**: Used to **retrieve emails from a server**, allowing access and manipulation from multiple devices.
    *   **POP3 (Post Office Protocol version 3)**: Used for **downloading emails from a server to a local client**, typically for single-device management.
*   **File Transfer and Management Protocols**:
    *   **FTP (File Transfer Protocol)**: Traditional protocol for **transferring files** over the Internet, used in website maintenance and large data transfers.
    *   **SSH (Secure Shell)**: Operates network services **securely on an unsecured network**. Commonly used for logging into a remote machine, executing commands, or transferring files.
*   **Real-time Communication Protocols**:
    *   **WebRTC (Web Real-Time Communication)**: Enables **browser-to-browser applications** for voice calling, video chat, and file sharing without plugins. Essential for video conferencing and live streaming.
    *   **MQTT (Message Queuing Telemetry Transport)**: Lightweight messaging protocol ideal for **IoT devices** and low-bandwidth scenarios.
    *   **AMQP (Advanced Message Queuing Protocol)**: Protocol for message-oriented middleware, providing robustness and security for enterprise-level message communication.
        *   **Example**: Used in tools like RabbitMQ.
*   **RPC (Remote Procedure Call)**:
    *   Allows a program on one computer to **execute code on a server or another computer as if it were a local call**.
    *   Abstracts network communication details, allowing seamless interaction with remote functions.
    *   Many application layer protocols use RPC mechanisms (e.g., HTTP requests resulting in backend RPC calls, SMTP servers using RPC calls internally).

### 9. API Design

API design defines inputs and outputs, focusing on how **CRUD (Create, Read, Update, Delete) operations** are exposed.

*   **CRUD Operations & Endpoints**:
    *   **Create**: **POST** request to `/api/products` with details in the request body.
    *   **Retrieve (all)**: **GET** request to `/api/products`.
    *   **Retrieve (single)**: **GET** request to `/api/products/{id}`.
    *   **Update**: **PUT** or **PATCH** request to `/api/products/{id}`.
    *   **Remove**: **DELETE** request to `/api/products/{id}`.
*   **Communication Protocol & Data Transport**: Decide on HTTP, WebSockets, or others, and data formats like JSON, XML, or Protocol Buffers.
*   **API Paradigms**:
    *   **REST (Representational State Transfer)**:
        *   **Stateless**: Each request contains all necessary information.
        *   Uses standard HTTP methods (GET, POST, PUT, DELETE).
        *   Easily consumable by various clients (browsers, mobile apps).
        *   **Downside**: Can lead to **over-fetching or under-fetching data**.
        *   Typically uses **JSON for data exchange**.
    *   **GraphQL**:
        *   Allows clients to **request exactly what they need**, avoiding over-fetching/under-fetching.
        *   Uses strongly typed queries.
        *   **Downside**: Complex queries can impact server performance.
        *   All requests are sent as **POST requests**.
        *   Responds with HTTP 200 even for errors, with error details in the response body.
    *   **gRPC (Google Remote Procedure Call)**:
        *   Built on **HTTP/2**, offering features like multiplexing and server push.
        *   Uses **Protocol Buffers for serializing structured data**, making it efficient in bandwidth and resources.
        *   Suitable for **microservices**.
        *   **Downside**: Less human-readable than JSON, requires HTTP/2 support.
*   **Endpoint Design**:
    *   Reflect relationships (e.g., `/users/{user_id}/orders` to fetch orders for a user).
    *   Include **limit and offset for pagination**, or start/end dates for filtering.
*   **Idempotency**: A well-designed **GET request should be idempotent**, meaning calling it multiple times doesn't change the result and always returns the same data. GET requests should never mutate data.
*   **Backward Compatibility**:
    *   When modifying endpoints, ensure changes **don't break existing clients**.
    *   **REST**: Introduce **new API versions** (e.g., `/v2/products`) to serve current clients while `v1` serves old ones.
    *   **GraphQL**: Add new fields without removing old ones to evolve the API.
*   **Rate Limiting**:
    *   Controls the **number of requests a user can make in a timeframe**.
    *   Prevents single users from sending too many requests and protects against DDoS attacks.
*   **CORS (Cross-Origin Resource Sharing)**:
    *   Controls which domains can access your API, **preventing unwanted cross-site interactions**.

### 10. Caching and CDNs

These are strategies to minimize request latency for distant users.

*   **Caching**: Storing a copy of data in temporary storage for faster future access.
*   **Browser Caching**:
    *   Stores website resources on a user's local computer.
    *   When revisiting a site, the browser loads from local cache instead of re-fetching.
    *   Stored in a directory on the client's hard drive, managed by the browser.
    *   Stores HTML, CSS, and JS bundle files.
    *   **`Cache-Control` header**: Tells the browser how long to cache content (e.g., `max-age=7200` for 2 hours).
    *   **Cache Hit**: Requested data found in cache.
    *   **Cache Miss**: Requested data not in cache, requires fetching from original source.
    *   **Cache Ratio**: Percentage of requests served from cache; higher ratio indicates more effective cache.
*   **Server Caching**:
    *   Stores frequently accessed data on the server side to **reduce expensive operations** (e.g., database queries).
    *   Stored on a server or a separate cache server (e.g., Redis for in-memory, or on disk).
    *   Server checks cache before querying the database.
    *   **Write Around Cache**: Data is written directly to permanent storage, bypassing the cache. Used when write performance is less critical.
    *   **Write Through Cache**: Data is simultaneously written to cache and permanent storage. Ensures data consistency but can be slower.
    *   **Write Back Cache**: Data is first written to cache, then to permanent storage later. Improves write performance but risks data loss on server crash.
    *   **Eviction Policies**: Rules to remove items when the cache is full.
        *   **Least Recently Used (LRU)**: Removes items not accessed for the longest time.
        *   **First In, First Out (FIFO)**: Removes items added first.
        *   **Least Frequently Used (LFU)**: Removes items used least often.
*   **Database Caching**:
    *   Caching database query results to improve performance.
    *   Done within the database system or via an external caching layer (e.g., Redis, Memcached).
    *   Beneficial for **read-heavy applications** with frequent queries.
    *   Uses the same eviction policies as server-side caching.
*   **CDN (Content Delivery Network)**:
    *   A **geographically distributed network of servers**.
    *   Serves **static content** (JavaScript, HTML, CSS, images, videos).
    *   Caches content from the origin server and delivers it from the **nearest CDN server** to the user.
    *   **Pull-based CDN**: CDN automatically pulls content from the origin server when first requested. Ideal for sites with regularly updated static content; requires less active management.
    *   **Push-based CDN**: User uploads content to the origin server, which then distributes files to the CDN. Useful for large, infrequently updated files that need quick distribution when changed; requires more active management.
    *   Also uses the `Cache-Control` header.
    *   **When CDN might not be used**: Dynamic content, real-time processing, or complex server-side logic.
*   **Benefits of Caching & CDNs**:
    *   **Reduced latency**: Content delivered from closer locations.
    *   **High availability and scalability**: Handle high traffic, resilient against failures.
    *   **Improved security**: DDoS protection, traffic encryption.
    *   **Lower server load**: Reduces requests to primary data source.
    *   **Faster load times**: Better user experience.

### 11. Proxy Servers

An **intermediary between a client and a server**.

*   **Purposes**: Caching, anonymizing requests, load balancing.
*   **Main Types**:
    *   **Forward Proxy**: Sits **in front of clients** to send requests to other internet servers. Often used in internal networks to control internet access.
        *   **Hides client's IP address**; request appears to come from the proxy.
        *   **Examples**:
            *   **Instagram proxies**: Manage multiple accounts appearing from different locations/users.
            *   **Internet use control**: Monitor and block employee access to non-work sites, scan for malware.
            *   **Caching**: Cache frequently accessed content, reducing bandwidth.
            *   **Anonymizing web access**: Hide IP address for privacy.
    *   **Reverse Proxy**: Sits **in front of one or more web servers**, intercepting client requests before they reach the servers.
        *   **Hides servers' identity/existence**.
        *   Distributes client requests across multiple servers (load balancing).
        *   Can compress data, cache files, manage SSL encryption.
        *   **Examples**:
            *   **Load Balancers**: Distribute traffic to prevent server bottlenecks.
            *   **CDNs**: Act as reverse proxies, caching content closer to users.
            *   **Web Application Firewalls (WAFs)**: Inspect traffic to block hacking attempts and protect applications from exploits.
            *   **SSL Offloading/Acceleration**: Handle encryption/decryption tasks, optimizing web server performance.
    *   **Open Proxy**: Allows any user to connect and use it for anonymous browsing or bypassing restrictions.
    *   **Transparent Proxy**: Passes requests without modification, but is visible to the client. Used for caching, content filtering.
    *   **Anonymous Proxy**: Identifiable as a proxy but does not reveal the original IP address.
    *   **Distorting Proxy**: Provides an incorrect original IP address.
    *   **High Anonymity/Elite Proxy**: Makes proxy detection difficult; does not send `X-Forwarded-For` or other identifying headers.

### 12. Load Balancers

The most popular use case of proxy servers. They **distribute incoming traffic across multiple servers** to prevent any single server from being overwhelmed, increasing application capacity and reliability.

*   **Algorithms/Strategies**:
    *   **Round Robin**: Each server gets a request sequentially. Works well for similar servers and uniform load.
    *   **Least Connections**: Directs traffic to the server with the **fewest active connections**. Ideal for longer tasks or uneven server loads.
    *   **Least Response Time**: Chooses the server with the **lowest response time and fewest active connections**. Aims for the fastest response.
    *   **IP Hashing**: Determines the server based on a **hash of the client's IP address**. Ensures a client consistently connects to the same server, useful for session persistence.
    *   **Weighted Algorithms**: Servers are assigned weights based on capacity/performance. More capable servers handle more requests (e.g., Weighted Round Robin, Weighted Least Connections).
    *   **Geographical Algorithms**: Directs requests to the server **geographically closest to the user**. Useful for global services to reduce latency.
    *   **Consistent Hashing**: Uses a hash function to distribute data across nodes (a "hash ring"). Ensures clients consistently connect to the same server.
*   **Health Checking**:
    *   Essential feature: **Continuously monitors servers** to ensure traffic is only directed to online and responsive servers.
    *   If a server fails, the load balancer stops sending traffic to it until it's back online.
*   **Forms**:
    *   **Hardware**: F5 Big-IP, Citrix NetScaler.
    *   **Software**: HAProxy, nginx.
    *   **Cloud-based**: AWS Elastic Load Balancing, Azure Load Balancer, Google Cloud's Load Balancer.
    *   **Virtual**: VMware Advanced Load Balancer.
*   **Handling Load Balancer Failure**: A load balancer is a **single point of failure**.
    *   **Redundant Load Balancing**: Use more than one load balancer (often in pairs) with **failover** (if one fails, the other takes over).
    *   **Continuous Monitoring and Health Checks**: Detect issues early.
    *   **Autoscaling and Self-healing Systems**: Automatically detect and replace failed load balancers.
    *   **DNS Failover**: Reroute traffic from a failed load balancer's IP to a standby IP.

### 13. Databases

*   **Types**:
    *   **Relational Databases (SQL)**:
        *   **Well-organized, uses tables for data storage, SQL as query language**.
        *   **Examples**: PostgreSQL, MySQL, SQLite.
        *   Great for **transactions, complex queries, and integrity**.
        *   **ACID Compliant**:
            *   **Atomicity (A)**: Transactions are **all or nothing**.
            *   **Consistency (C)**: Database remains in a **consistent state** after a transaction.
            *   **Isolation (I)**: Transactions are **independent**.
            *   **Durability (D)**: Once committed, data is **there to stay**.
    *   **NoSQL Databases**:
        *   More **flexible, schema-less** (no foreign keys).
        *   **Examples**: MongoDB, Cassandra, Redis.
        *   Different types: **key-value pairs** (Redis), **document-based** (MongoDB), **graph-based** (Neo4j).
        *   Good for **unstructured data, scalability, quick iteration, and simple queries**.
        *   **Drops consistency property from ACID** (can sacrifice C for A and P, as per CAP theorem).
    *   **In-memory Databases**:
        *   **Fast** because everything is in memory.
        *   **Examples**: Redis, Memcached.
        *   Used primarily for **caching and session storage** due to lightning-fast data retrieval.
*   **Scaling Databases**:
    *   **Vertical Scaling (Scale Up)**:
        *   Improve performance by **enhancing individual server capabilities** (e.g., increasing CPU, RAM, faster storage).
        *   **Limited** due to maximum resources a single machine can hold.
    *   **Horizontal Scaling (Scale Out)**:
        *   **Adding more machines** to the existing pool.
        *   Distributes data across a cluster of machines.
        *   Involves **database sharding or data replication**.
            *   **Database Sharding**: Distributes different portions (**shards**) of data across multiple servers. Splits data into smaller chunks.
                *   **Range-based sharding**: Distributes data based on a key's range.
                *   **Directory-based sharding**: Uses a lookup service to direct traffic to the correct database.
                *   **Geographical sharding**: Splits databases based on location.
            *   **Data Replication**: Keeps **copies of data on multiple servers** for high availability.
                *   **Master-Slave replication**: One master database (read/write) and several read-only slave databases.
                *   **Master-Master replication**: Multiple databases that can both read and write.
*   **Database Performance Techniques**:
    *   **Caching**: Use in-memory databases like Redis to cache frequent queries and boost performance.
    *   **Indexing**: Create indexes for frequently accessed columns to significantly speed up retrieval times.
    *   **Query Optimization**: Minimize joins, use tools like SQL query analyzer or explain plans to understand and improve query performance.

Remember, when designing a system, prioritize two of the CAP theorem properties (Consistency, Availability, Partition Tolerance) based on your specific requirements.