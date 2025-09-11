Here are detailed revision notes explaining the concepts presented in the webpage:

### Detailed Revision Notes: How Web Servers Work

#### 1. Introduction to Web Servers and Clients

*   **The Internet as an Information Source**: The internet provides a vast amount of information, which is retrieved by querying it.
*   **Web Servers**: These are fundamental to how we receive information from the internet. They are primarily **simple computer programs that dispense web pages when requested**.
    *   The machines running these programs are often called servers, and the terms "web server" and "server" are frequently used interchangeably.
    *   While some high-powered computers are built for web hosting (handling multiple domains/websites on a single server), normally, a "web server" refers to the **software** that can be downloaded onto a computer system.
*   **Web Clients**: These are applications that users employ to interact with the web, browse, and retrieve files from web servers.
    *   Examples include web browsers like Internet Explorer, Mozilla Firefox, Chrome, and Safari.

#### 2. When are Web Servers Required?

Web servers are typically used by web hosting companies and professional web app developers, but they can also be utilised by others.

*   **Website Owners**: To create a local copy of their website on their system that mirrors the online version.
*   **Developers using Server-Side Technologies**: For those who want to use technologies such as PHP or ColdFusion.
*   **Local vs. Public Hosting**:
    *   An individual using a web server will typically **locally host** a website, meaning its contents are accessible only on their local system.
    *   Web hosting provider companies host websites so they can be **viewed globally**.
    *   Individuals *can* publicly host a website with their web server, but it requires a **leased line internet connection** (for a dedicated IP address) and a **DNS server** to link it with the website's domain. This is generally not preferred due to security concerns.

#### 3. How Web Servers Work: The 4-Step Process

Viewing a page on the internet involves a four-step process where the browser requests information from the web server, and the server responds.

1.  **Obtaining the IP Address from the Domain Name**:
    *   Your web browser first needs to find the **IP address** associated with a domain name (e.g., www.geeksforgeeks.org).
    *   This can be done in two ways:
        *   **Searching its cache**: The browser first checks its own stored information.
        *   **Requesting one or more DNS (Domain Name System) Servers**: If not in cache, the browser queries DNS servers to resolve the domain name to an IP address.

2.  **Browser Requests the Full URL**:
    *   Once the IP address is known, the browser sends a request for the **full URL** to the web server.

3.  **The Web Server Responds to the Request**:
    *   The web server processes the browser's request and sends the **desired web pages** back.
    *   If the pages don't exist or an error occurs, it sends an **appropriate error message**.
        *   **Error 404**: Sent when the requested page does not exist.
        *   **Error 401**: Sent when access is denied, often due to incorrect credentials like username or password.

4.  **The Browser Displays the Web Page**:
    *   Finally, the browser receives the web pages (or error message) and **displays it** to the user.

#### 4. Performance Measures of Web Servers

Several parameters are used to define and evaluate the performance of a web server under various loads, requests, and responses.

*   **RPS (Requests per Second)**:
    *   Determines the **maximum number of requests a server can handle** from different clients.
    *   Influenced by factors like the HTTP version and the type of HTTP requests.
*   **Latency**:
    *   Represents the **response time** a server takes to process each client's request.
    *   Calculated in **milliseconds**.
    *   For an ideal server, latency should be **very low**.
*   **Throughput**:
    *   Defined as the **amount of data transferred in a given amount of time**.
    *   Calculated in **bytes per second**.
    *   For an ideal server, throughput should be **very high**.
*   **Concurrency**:
    *   Used to check performance because RPS, latency, and throughput can fluctuate significantly based on the **number of active clients and connections**.
    *   Supported by web servers under various specifications, including server configuration, operating system type, and hardware resources.

#### 5. Popular Web Servers

While there are several web servers available (e.g., Apache, Microsoft IIS, Nginx, LightSpeed), two are particularly popular.

*   **Apache HTTP Server**:
    *   The **most popular** and widely used web server.
    *   Developed and maintained by the **Apache Software Foundation**.
    *   It is **free and open source**, produced under the Apache License.
    *   Available for a wide range of operating systems, including Windows, Mac OS X, Unix, Linux, Solaris, Novell Netware, and FreeBSD.
*   **Microsoft Internet Information Service (IIS)**:
    *   The **second most popular** web server, with rapidly increasing market share.
    *   Developed and maintained by **Microsoft**.
    *   It has features similar to Apache but is **not open source**.
    *   Works exclusively with **Windows operating system platforms**.

#### 6. Related Computer Science and Networking Concepts (Context from the Webpage Structure)

The webpage where this information is found is part of a larger platform, GeeksforGeeks, which offers tutorials and courses across various computer science domains. These areas provide the broader context for understanding web servers:

*   **Web Development**: Web servers are a core component of web development.
*   **Computer Networks**: The entire functioning of web servers relies heavily on computer networking principles, including:
    *   **Network Models**: OSI Model, TCP/IP Model.
    *   **Network Layers**: Physical Layer, Data Link Layer, Network Layer (including IP Addressing, Routing, Protocols), Transport Layer (TCP, UDP), Session Layer, Presentation Layer, Application Layer (Client-Server Model, WWW, Email, Application Layer Protocols).
    *   **Network Security**: Concepts like firewalls, encryption, authentication, and VPNs (like PPTP) are crucial for secure web server operation.
*   **Data Structures & Algorithms (DSA)**: Often foundational for efficient server-side programming.
*   **Programming Languages**: Essential for developing web applications that run on web servers (e.g., Python, Java, C++, PHP mentioned implicitly).
*   **Operating Systems**: Web servers run on specific operating systems (e.g., Windows, Linux for Apache/IIS).
*   **DevOps and Cloud Computing**: Modern deployment and management of web servers frequently involve DevOps practices and cloud platforms.