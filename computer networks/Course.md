

### **I. Introduction to Computer Networking**
*   **Importance**: Computer networking is crucial for all developers (mobile, web, DevOps) to understand how things work internally.
*   **Mindset**: A great developer needs to have curiosity about how computers, RAM, the internet, and web pages function.
*   **Learning Approach**: The course aims to make learning fun through a storytelling format, covering basic concepts, history, and technical deep dives.

### **II. Basic Definitions**
*   **Computer**: Commonly Oriented Machine Particularly Used for Training Education and Research (full form).
*   **Network**: Computers connected together.
*   **Internet**: A global collection of interconnected computer networks, spanning houses, cities, and countries.

### **III. History of the Internet**
*   **Cold War Era**: The internet's origins are tied to the Cold War rivalry between the United States and the Soviet Union.
    *   **Sputnik (1957)**: The Soviet Union launched the first satellite, prompting the US to seek technological advantage.
    *   **ARPA (Advanced Research Projects Agency)**: Created by the US government to drive scientific discoveries and maintain global leadership.
    *   **ARPANET**: Developed by ARPA to enable communication between its facilities. Initial connections included MIT, Stanford, UCLA, and the University of Utah. Early ARPANET focused on research and communication among connected locations.
*   **World Wide Web (WWW)**:
    *   **Problem**: Early ARPANET lacked automated sharing of documents, especially those referencing other documents.
    *   **Tim Berners-Lee**: Developed the **World Wide Web** to store and access documents via hyperlinks.
    *   **First Website**: info.cern.ch.
    *   **Components**: Documents and web resources identified by **URLs**, interconnected by **hyperlinks**, and accessible over the internet via **web servers**.
*   **Evolution**: The need for discovery led to the development of **search engines** (e.g., Yahoo, though the first is debated).

### **IV. Protocols**
*   **Definition**: A set of rules and regulations that define how data is transferred and how applications communicate with each other over the internet.
*   **Importance**: Essential for inter-application communication, preventing chaos if every application had different rules.
*   **Standardization**: The **Internet Society** is responsible for creating and controlling these rules, accepting submissions via **RFCs (Request for Comments)**.
*   **Examples**:
    *   **TCP (Transmission Control Protocol)**: Ensures 100% data delivery, ordered, and uncorrupted.
    *   **UDP (User Datagram Protocol)**: Faster, but does not guarantee 100% data delivery or order (e.g., video conferencing where some data loss is acceptable).
    *   **HTTP (Hypertext Transfer Protocol)**: Used by web browsers and the WWW to define data format between web clients and servers.
    *   **DHCP (Dynamic Host Configuration Protocol)**: Assigns IP addresses to devices on a network.
    *   **FTP (File Transfer Protocol)**: For transferring files.
    *   **SMTP (Simple Mail Transfer Protocol)**: Used to send emails.
    *   **POP3 (Post Office Protocol version 3) & IMAP (Internet Message Access Protocol)**: Used to receive emails.
    *   **SSH (Secure Shell)**: For secure remote terminal access.
    *   **Telnet**: Terminal emulation protocol, connecting to a remote host (Port 23).

### **V. Client-Server Architecture**
*   **Core Concept**: A client (your computer) sends a **request** to a server (e.g., Google's server), and the server sends back a **response** (e.g., a web page).
*   **Localhost**: Your own computer can act as both a client and a server.
*   **Data Centers**: Large collections of servers used by big companies (YouTube, Facebook) to handle numerous requests, providing high availability and static IP addresses. Often rented out by **cloud providers**.
*   **Ping**: A utility to measure the round-trip time for messages sent to a destination and echoed back. Shows data in chunks (packets), sequence numbers, and Time To Live (TTL). Ping time cannot be reduced as signals travel at the speed of light.

### **VI. Peer-to-Peer (P2P) Architecture**
*   **Concept**: Applications on various devices connect directly with each other, without a central server or data center.
*   **Advantages**: Rapid scalability, decentralized network.
*   **Example**: BitTorrent (where each peer acts as both a client and a server, "seeding" and "leeching").
*   **Hybrid Models**: Combine P2P with some centralized components.

### **VII. Addressing on the Internet**
*   **IP Addresses (Internet Protocol Address)**:
    *   **Definition**: A unique numerical label assigned to every device (computer, server, router) on a computer network that uses the Internet Protocol for communication. It's like a phone number for devices.
    *   **Format**: Typically four sets of numbers separated by dots (e.g., 192.168.1.1), with each number ranging from 0 to 255.
    *   **Global IP Address**: Your Internet Service Provider (ISP) assigns a single global IP address to your modem/router.
    *   **Local IP Addresses**: The modem/router then assigns unique local IP addresses to devices within your home network using **DHCP**. From the internet's perspective, all devices on your Wi-Fi share the same global IP.
    *   **Purpose**: Identifies the specific **device**.
*   **Port Numbers**:
    *   **Definition**: A 16-bit number that identifies a specific **application** or service running on a device.
    *   **Range**: 2^16, approximately 65,000 possible port numbers.
    *   **Well-known Ports (0-1023)**: Reserved for common services (e.g., Port 80 for HTTP). You cannot host your own application on these.
    *   **Registered Ports (1024-49152)**: Registered for specific applications (e.g., MongoDB, MySQL).
    *   **Ephemeral Ports**: Randomly assigned on the client side for multiple instances of an application (e.g., multiple Chrome tabs). Freed after use.
    *   **Purpose**: Identifies the specific **application** on a device.
*   **Sockets**:
    *   **Definition**: A software process interface that acts as a connection point between an application process and the internet. Applications communicate through sockets, which are tied to port numbers.

### **VIII. Data Transmission Fundamentals**
*   **Data in Chunks**: Data is not sent all at once but in smaller units (packets, segments, frames).
*   **Speed Measurement**:
    *   **Mbps (Megabits per second)**: Refers to data transfer rate, where 1 Mbps is 1 million bits per second.
    *   **Gbps (Gigabits per second)**: 10^9 bits per second.
    *   **Kbps (Kilobits per second)**: 1000 bits per second.
    *   **Upload**: Sending data from your computer.
    *   **Download**: Receiving data to your computer.
*   **Physical Connectivity**:
    *   **Guided Media**: Physical wires or cables provide a defined path for data.
        *   **Submarine Cables**: Optical fiber cables laid across ocean floors connect continents. They are faster than satellite communication, heavily guarded, and often buried to prevent damage. Major entities like Google own many of these.
        *   **Optical Fiber Cables**: Use light signals for fast data transmission over long distances.
        *   **Coaxial Cable**: Another type of guided cable.
        *   **Ethernet Cable**: Commonly used for local wired connections.
    *   **Unguided Media (Wireless)**: Communication without a physical path.
        *   **Short Range**: Bluetooth, Wi-Fi.
        *   **Long Range**: 3G, 4G (LTE), 5G, satellite communication (though slower than cables).

### **IX. Network Types (High School Refresher)**
*   **LAN (Local Area Network)**: Connects devices in a small area (e.g., home, office). Can connect thousands of computers within a localized area.
*   **MAN (Metropolitan Area Network)**: Covers a larger area, such as a city.
*   **WAN (Wide Area Network)**: Connects networks across countries, often using optical fiber cables.
*   **The Internet** is a global collection of interconnected LANs, MANs, and WANs.
*   **SONET (Synchronous Optical Networking)**: Carries data over optical fiber cables for large distances.
*   **Frame Relay**: A WAN technology connecting LANs to a wider area network.

### **X. Network Devices**
*   **Modem**: Converts digital signals from a computer into analog signals for transmission over media (like telephone lines) and vice versa.
*   **Router**: A device that routes data packets between different networks based on their IP addresses. Operates at the Network Layer.
*   **Repeater**: A physical layer device that regenerates (copies bit-by-bit) a signal over the same network to prevent it from becoming too weak or corrupted. Does not amplify.
*   **Hub**: A multi-port repeater, connecting multiple devices in a star topology. It broadcasts data to all connected devices and cannot filter data packets.
*   **Bridge**: Operates at the Data Link Layer. It's a repeater with the added functionality to filter data by reading MAC addresses of source and destination.
*   **Switch**: A multi-port bridge, also at the Data Link Layer. Improves performance and efficiency by performing error checking and intelligently forwarding data to the correct port based on MAC addresses.
*   **Gateway**: A passage that connects two networks, especially those that might operate on different networking models or protocols.
*   **Brouter**: A device that combines the functionalities of a bridge and a router.
*   **Network Adapter/Card**: Manages connections to the outside world via Wi-Fi, Bluetooth, or Ethernet.

### **XI. Network Topologies (High School Refresher)**
*   **Bus Topology**: All systems connect to a single backbone cable. Simple, but a break in the backbone can disrupt the entire network. Only one device can transmit data at a time.
*   **Ring Topology**: Computers are connected in a closed loop. Data travels in one direction. A single cable break can disrupt the entire network. Data may pass through unnecessary nodes.
*   **Star Topology**: All computers connect to a central device (e.g., a hub or switch). If the central device fails, the entire network goes down.
*   **Tree Topology**: A hierarchical structure combining elements of bus and star topologies, offering more fault tolerance than a simple bus.
*   **Mesh Topology**: Every computer is directly connected to every other computer. Highly fault-tolerant but expensive and difficult to scale due to the large number of cables required.

### **XII. The OSI Model (Open Systems Interconnection Model)**
*   **Purpose**: A conceptual framework that standardizes how two or more computers communicate. It breaks down the complex process of network communication into seven distinct layers.
*   **Layers (from top to bottom on sender, bottom to top on receiver):**

1.  **Application Layer (Layer 7)**:
    *   **Function**: The layer users directly interact with. Provides network services to end-user applications.
    *   **Data Unit**: Messages, files, emails.
    *   **Responsibilities**: User interface, application-specific protocols.
    *   **Protocols**:
        *   **HTTP/HTTPS**: For web browsing (client-server protocol, defines request/response, uses TCP).
            *   **Stateless**: HTTP does not store client information by default.
            *   **HTTP Methods**: GET (request data), POST (submit data), PUT (place data), DELETE (remove data).
            *   **Status Codes**: Indicate request outcome (e.g., 200 OK, 404 Not Found, 500 Server Error).
            *   **Cookies**: Small unique strings stored on the client's browser to maintain state (e.g., login sessions, cart items). Sent with subsequent requests. Can have expiration dates. Third-party cookies can track users across sites.
        *   **SMTP**: Sends emails (uses TCP for reliability).
        *   **POP3/IMAP**: Receives emails. POP3 downloads and can delete from server (client-specific access). IMAP syncs across multiple devices, keeping emails on the server.
        *   **DNS (Domain Name System)**: Translates human-readable domain names (e.g., google.com) into numerical IP addresses. Acts like the internet's phone book.
            *   **Process**: Browser checks local cache -> local DNS server (ISP) -> root DNS server -> Top-Level Domain (TLD) server (.com, .org) -> resolves to IP.
            *   **Domain Structure**: Subdomain (mail.google.com), Second-level domain (google.com), Top-level domain (.com).
            *   **ICANN**: Internet Corporation for Assigned Names and Numbers, manages TLDs.
            *   **Domain Ownership**: Domains are rented, not bought.
        *   FTP, Telnet.
    *   **Programs, Processes, Threads**:
        *   **Program**: An application (e.g., WhatsApp).
        *   **Process**: A running instance of a program or one of its features (e.g., sending a message, recording a video).
        *   **Thread**: A lighter version of a process, performing a single job within a process (e.g., setting up a page).

2.  **Presentation Layer (Layer 6)**:
    *   **Function**: Ensures data is in a usable format for the Application Layer. Handles data formatting and conversion.
    *   **Responsibilities**:
        *   **Translation**: Converts data into a machine-representable binary format (e.g., ASCII to EBCDIC).
        *   **Encryption/Decryption**: Secures data (e.g., using SSL/TLS).
        *   **Compression**: Reduces data size for efficient transmission.
        *   **Abstraction**: Provides a consistent data format to the Application Layer.

3.  **Session Layer (Layer 5)**:
    *   **Function**: Establishes, manages, and terminates communication sessions between applications on different devices.
    *   **Responsibilities**:
        *   **Authentication/Authorization**: Verifies user identity and permissions to access server resources.
        *   **Session Maintenance**: Manages the dialogue (e.g., maintaining a shopping cart session on an e-commerce website).

4.  **Transport Layer (Layer 4)**:
    *   **Function**: Ensures reliable and ordered delivery of data to the correct **application** on the destination device. It focuses on end-to-end communication between applications.
    *   **Data Unit**: **Segments**.
    *   **Responsibilities**:
        *   **Segmentation**: Divides data from the Session Layer into smaller segments. Each segment includes source/destination port numbers and a sequence number.
        *   **Multiplexing**: Sends multiple application data streams over a single network connection (on sender side).
        *   **Demultiplexing**: Delivers received segments to the correct application based on port numbers (on receiver side).
        *   **Flow Control**: Manages data transfer rate to prevent a fast sender from overwhelming a slow receiver.
        *   **Error Control**: Detects and handles lost or corrupted data segments (e.g., using **checksums** to verify data integrity).
        *   **Congestion Control**: Prevents network overload by adjusting data transmission rates.
        *   **Sequence Numbers**: Ensures segments are reassembled in the correct order and identifies duplicate packets.
        *   **Timers & Retransmission**: Uses timers (retransmission timer) to detect lost packets; if an acknowledgment isn't received within the timer, the packet is re-sent.
    *   **Protocols**:
        *   **TCP (Transmission Control Protocol)**:
            *   **Connection-Oriented**: Establishes a connection (three-way handshake) before data transfer.
            *   **Reliable**: Guarantees 100% data delivery, order, and error-free transmission.
            *   **Features**: Error control, flow control, congestion control, full-duplex communication (data can be sent in both directions simultaneously).
            *   **Three-Way Handshake**: Client sends SYN (synchronization flag) + sequence number; Server responds with SYN-ACK (acknowledgment of SYN + its own SYN) + sequence number; Client responds with ACK (acknowledgment of SYN-ACK) + acknowledgement number. Sequence numbers are random for security.
            *   **Use Cases**: Email (SMTP, POP3, IMAP), File Transfer, Web Browsing (HTTP uses TCP).
        *   **UDP (User Datagram Protocol)**:
            *   **Connectionless**: No connection established before sending data.
            *   **Unreliable**: Data may be lost, duplicated, or arrive out of order.
            *   **Faster**: Due to less overhead.
            *   **Uses Checksums**: To detect corrupted data, but doesn't fix or re-send.
            *   **Use Cases**: Video conferencing, online gaming, DNS lookups (where speed is critical and minor loss is acceptable).

5.  **Network Layer (Layer 3)**:
    *   **Function**: Responsible for logical addressing and routing data packets between **different networks** (source to destination across the internet). It's where routers operate.
    *   **Data Unit**: **Packets**.
    *   **Responsibilities**:
        *   **Logical Addressing (IP Addressing)**: Assigns source and destination IP addresses to packets.
            *   **IPv4**: 32-bit numbers, providing ~4.3 billion unique addresses. Divided into classes (A, B, C, D, E) based on ranges..
            *   **IPv6**: 128-bit numbers, the future of IP addressing, providing vastly more unique addresses. Represented in hexadecimal. Not backward compatible with IPv4, requiring significant infrastructure changes.
            *   **Subnetting**: Divides an IP network into smaller subnetworks (network address + host address). Subnet masks identify the network portion. IP address allocation to ISPs is based on regions to minimize hops.
            *   **Reserved Addresses**: Special addresses like 127.0.0.1 (Localhost) for loopback communication.
        *   **Routing**: Determines the best path for data packets from source to destination.
            *   **Routers**: Use **routing tables** (which contain multiple paths to destinations) and **forwarding tables** (which specify a single, faster path for specific destinations).
            *   **Hop-by-Hop Forwarding**: Packets are forwarded from router to router until they reach the destination network.
            *   **Control Plane**: Responsible for building and updating routing tables.
                *   **Static Routing**: Manual configuration of routes, not adaptive.
                *   **Dynamic Routing**: Algorithms (e.g., Bellman-Ford, Dijkstra) automatically update routes based on network changes.
        *   **Load Balancing**: Distributes network traffic across multiple paths to prevent overload.
        *   **Time To Live (TTL)**: A value in the IP packet header that limits the number of hops a packet can take before being discarded, preventing infinite loops in the network.
    *   **Middle Boxes**: Devices that interact with IP packets beyond end systems and routers.
        *   **Firewall**: Filters, rejects, or modifies packets based on rules (IP addresses, port numbers, flags). Can be stateless or stateful (maintains connection state for efficiency).
        *   **NAT (Network Address Translation)**: Maps private IP addresses within a local network to a single public IP address for external communication. This helps conserve public IP addresses and adds a layer of security.

6.  **Data Link Layer (Layer 2)**:
    *   **Function**: Provides reliable data transfer across a **physical link** between directly connected devices (e.g., within a LAN or between a computer and a router).
    *   **Data Unit**: **Frames**.
    *   **Responsibilities**:
        *   **Physical Addressing (MAC Addressing)**: Assigns source and destination **MAC (Media Access Control) addresses** to frames.
            *   **MAC Address**: A 12-digit alphanumeric number unique to a network interface (e.g., Wi-Fi card, Bluetooth adapter). It identifies the specific hardware component.
            *   **ARP (Address Resolution Protocol)**: Maps an IP address to its corresponding MAC address within a local network (e.g., device 1 needs MAC of device 4, it broadcasts a request).
        *   **Framing**: Structures the data into frames, including MAC addresses, for transmission.
        *   **Error Detection**: Detects errors in the transmitted frames.
        *   **Media Access Control**: Regulates how devices access the shared physical medium.

7.  **Physical Layer (Layer 1)**:
    *   **Function**: Concerned with the physical transmission of raw bits (zeros and ones) over a physical medium.
    *   **Data Unit**: **Bits** (electrical, light, or radio signals).
    *   **Responsibilities**: Defines hardware specifications (cables, connectors, voltage levels, data rates). Converts digital bits into signals suitable for the transmission medium (e.g., electrical pulses for copper wires, light pulses for fiber optics, radio waves for Wi-Fi).

### **XIII. Order of Execution (OSI Model)**
*   **Sender**: Data originates at the Application Layer, flows down through Presentation, Session, Transport, Network, Data Link, and finally to the Physical Layer, where it is converted into signals for transmission.
*   **Receiver**: The Physical Layer receives the signals, converts them back to bits, and passes them up through the Data Link, Network, Transport, Session, Presentation, and finally to the Application Layer, where the friend receives the message.
*   **Conceptual Peers**: Each layer on the sender conceptually "communicates" with its corresponding peer layer on the receiver.

### **XIV. TCP/IP Model (Internet Protocol Suite)**
*   **Alternative Model**: Developed by ARPA, more widely used in practice than the conceptual OSI model.
*   **Layers**: It has five layers:
    1.  **Application Layer**: Combines OSI's Application, Presentation, and Session layers.
    2.  **Transport Layer**
    3.  **Network Layer**
    4.  **Data Link Layer**
    5.  **Physical Layer**

### **XV. Program, Process, and Thread**
*   **Program**: An application, such as WhatsApp or Amazon.
*   **Process**: A running instance of a program or a specific feature of a program (e.g., sending a message, recording a video). One program can have many processes.
*   **Thread**: A lighter-weight version of a process, typically performing a single job within a process. Multiple threads can run simultaneously within a single process (multi-threading).

