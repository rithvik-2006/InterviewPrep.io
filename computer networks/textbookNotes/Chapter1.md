Here are detailed revision notes for Chapter 1, "Introduction," from "Andrew S. Tanenbaum - Computer Networks, Fifth Edition".

**Chapter 1: Introduction**
**Authors:** Andrew S. Tanenbaum and David J. Wetherall

**Overview and Key Themes:**
This introductory chapter sets the stage for the entire book, providing a foundational understanding of computer networks. It covers various aspects, from the applications of networks to their underlying hardware and software structures, different reference models, and examples of real-world networks. The fifth edition specifically updates content on the Internet, mobile phone networks, 802.11 (WiFi), and RFID/sensor networks.

**1.1 Uses of Computer Networks**
Computer networks serve numerous purposes for both businesses and individuals, both at home and on the go.

*   **Business Applications:**
    *   Companies use networks to share corporate information, often employing a **client-server model** where desktop computers act as clients accessing powerful servers.
*   **Home Applications:**
    *   Networks offer individuals access to diverse information and entertainment, as well as platforms for buying and selling products and services.
    *   Access to the Internet is typically via phone or cable providers, with increasing use of **wireless access** for laptops and phones.
*   **Mobile Users:**
    *   Technology advancements are enabling new mobile applications and networks with computers embedded in various devices.
*   **Social Issues:**
    *   These advancements also raise social concerns, such as **privacy**.

**1.2 Network Hardware**
A **computer network** is defined as a collection of autonomous computers interconnected by a single technology, allowing them to exchange information. Interconnections can use various media, including copper wire, fiber optics, microwaves, infrared, and communication satellites. Networks are often connected to form larger networks, with the Internet being the most famous example of a **"network of networks"**.

Networks are classified by their scale:

*   **Personal Area Networks (PANs):**
    *   These are for individual use, typically within a few meters.
    *   **Bluetooth** is a common technology for PANs, connecting devices like phones to headsets or computers to peripherals.
    *   **RFID** (Radio Frequency IDentification) can also form PANs for short-range communication, such as on smartcards or library books.
*   **Local Area Networks (LANs):**
    *   Cover a single building or campus, generally within 10 meters to 1 kilometer.
    *   Speeds range from 10 Mbps to gigabits per second.
    *   **Wireless LANs** use **IEEE 802.11 (WiFi)**, with speeds from 11 to hundreds of Mbps.
    *   **Switched Ethernet** is a common wired LAN technology, where switches forward packets based on logical separation, enabling **Virtual LANs (VLANs)**.
    *   **Security** is a significant concern for home networks, where the choice between wired and wireless networks presents trade-offs between convenience/cost and security.
*   **Metropolitan Area Networks (MANs):**
    *   Cover a city, spanning 10 to 100 kilometers.
*   **Wide Area Networks (WANs):**
    *   Cover countries or continents, spanning 100 to 10,000 kilometers.
    *   Often consist of hosts connected to a **subnet**, which comprises routers and communication lines that move packets between hosts.
    *   **Virtual Private Networks (VPNs)** are overlays that use the underlying capacity of the Internet to provide a measure of security and flexible reuse of resources, though with a lack of control over underlying resources.
    *   **Routing algorithms** determine the path for communication, and **forwarding algorithms** decide where to send a packet next.
*   **Internetworks (Internet):**
    *   A collection of interconnected networks, often with different hardware and software, allowing communication between them.
    *   The **Internet** (capitalized) is the most well-known specific example, connecting enterprise, home, and other networks through ISP networks.
    *   The concept of **Interplanetary Internet** is also being explored.

**1.3 Network Software**
Network software is highly structured to manage complexity.

*   **Protocol Hierarchies:**
    *   Most networks are organized as a **stack of layers or levels**, each building upon the one below it.
    *   Each layer offers services to higher layers while hiding implementation details, acting as a "virtual machine".
    *   A **network architecture** defines a set of layers and protocols, specifying enough information for correct protocol obedience without revealing implementation details or interface specifications.
    *   A **protocol stack** is a list of protocols used by a system, one per layer.
    *   Communication involves **peer processes** at each layer, with data passing down through interfaces and headers/trailers added at each layer before transmission and stripped off upon reception. Lower layers of a hierarchy are often implemented in hardware or firmware.
*   **Design Issues for the Layers:**
    *   **Reliability:** Networks must operate correctly despite unreliable components. This involves **error detection** (e.g., retransmission of damaged information) and **error correction** (recovering the correct message from incorrect bits, using redundant information). These mechanisms are used at both low and high layers.
    *   **Security:** Defending against threats like **eavesdropping** (confidentiality), **impersonation** (authentication), and **message alteration** (integrity). These designs are based on **cryptography**, which is covered in detail in Chapter 8.
*   **Connection-Oriented Versus Connectionless Service:**
    *   **Connection-oriented service:** Modeled after the telephone system; requires establishing, using, and then releasing a connection. It acts like a "tube" where order is preserved. Parameters like message size and quality of service (QoS) can be negotiated during establishment. Can be **reliable** (data never lost, typically with acknowledgements) or **unreliable** (e.g., unreliable connection-oriented audio).
    *   **Connectionless service:** No prior setup is needed. Can be **reliable** (e.g., acknowledged datagram service like text messaging) or **unreliable** (**datagram service**, which is dominant in most networks).
    *   **Request-reply service:** A sender transmits a datagram request, and the reply contains the answer, commonly used in client-server models.
*   **Service Primitives:**
    *   Operations provided by a layer to the layer above it (e.g., CONNECT, ACCEPT, SEND, RECEIVE, DISCONNECT).
*   **The Relationship of Services to Protocols:**
    *   A **service** defines what a layer does, its semantics.
    *   An **interface** specifies how to access a layer, including parameters and expected results.
    *   A **protocol** defines the rules governing communication between peer entities at the same layer in different machines. The OSI model made the distinction between these three concepts explicit.

**1.4 Reference Models**
Two important network architectures are discussed: the OSI reference model and the TCP/IP reference model. The OSI model is strong in its general model, while the TCP/IP model is strong in its widely used protocols. The book uses a **hybrid model**.

*   **The OSI Reference Model:**
    *   Has **seven layers**, designed with principles like requiring a different abstraction per layer, well-defined functions, and internationally standardized protocols.
    *   **Layers:** Physical, Data Link, Network, Transport, Session, Presentation, Application.
    *   **Physical Layer:** Concerned with transmitting raw bits over a communication channel, dealing with electrical, mechanical, and timing interfaces, and the physical medium.
*   **The TCP/IP Reference Model:**
    *   Has **four layers**: Host-to-network, Internet, Transport, and Application.
    *   **Protocols** include IP (Internet Protocol) at the Internet layer, TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) at the Transport layer, and HTTP, DNS, and RTP at the Application layer.
*   **The Model Used in This Book:**
    *   A **five-layer hybrid model**: Physical, Link, Network, Transport, Application.
    *   **Physical layer:** Transmits bits across media as electrical/analog signals.
    *   **Link layer:** Sends finite-length messages between directly connected computers with specified reliability (e.g., Ethernet, 802.11).
    *   **Network layer:** Combines multiple links into networks and internetworks, handling packet routing (e.g., IP).
    *   **Transport layer:** Strengthens delivery guarantees, providing reliable byte streams or other abstractions for applications (e.g., TCP).
*   **A Comparison of the OSI and TCP/IP Reference Models:**
    *   Fundamental similarities but many differences, especially concerning services, interfaces, and protocols.
*   **A Critique of the OSI Model and Protocols:**
    *   OSI protocols did not dominate due to factors like bad timing in standardization, poor technology choices, and poor implementations.
    *   The timing of standards development is crucial, needing to be between the early research phase and major industry investment (the "apocalypse of the two elephants").

**1.5 Example Networks**
This section provides an idea of the variety in computer networking.

*   **The Internet:**
    *   A vast collection of networks using common protocols and services, not centrally planned or controlled.
    *   Originated from the **ARPANET**, a DoD project for a survivable command-and-control network, contrasting with the vulnerable public telephone network.
*   **Third-Generation Mobile Phone Networks (3G):**
    *   Have a different architecture from the Internet, based on cellular design.
    *   The **air interface** (radio communication protocol between mobile device and base station) is crucial. UMTS (Universal Mobile Telecommunications System) air interface uses **Code Division Multiple Access (CDMA)**.
    *   Future mobile networks are increasingly adopting Internet protocols (IP and packets) for voice and data.
*   **Wireless LANs: 802.11 (WiFi):**
    *   Dominant standard for wireless LANs, popular in homes and public places.
    *   Different versions (802.11b, 802.11a/g) use various modulation schemes like **OFDM** (Orthogonal Frequency Division Multiplexing) to boost bit rates.
    *   **Multipath fading** is a challenge in wireless communication, where signals take multiple paths, leading to interference.
*   **RFID and Sensor Networks:**
    *   **RFID** (Radio Frequency IDentification) tags and readers extend network reach to everyday objects.
    *   Types include **UHF RFID** (e.g., 902-928 MHz in US, using **backscatter** communication) and **HF RFID** (e.g., 13.56 MHz, short-range, based on **induction**), as well as **LF RFID**.
    *   **Sensor nodes** are small, battery-powered computers with sensors that self-organize into **multihop networks** to relay information. Energy efficiency is a key challenge.

**1.6 Network Standardization**
Standards are crucial for **interoperability**, allowing a larger market and product competition.

*   **Who’s Who in the Telecommunications World:**
    *   **ITU (International Telecommunication Union):** A UN agency for telecommunication standards, with three sectors: ITU-T (Telecommunications Standardization Sector), ITU-R (Radiocommunications Sector), and ITU-D (Development Sector).
*   **Who’s Who in the International Standards World:**
    *   **ISO (International Standards Organization):** A global organization producing various standards.
*   **Who’s Who in the Internet Standards World:**
    *   **IAB (Internet Architecture Board):** Oversees Internet development.
    *   **RFCs (Request For Comments):** Technical reports documenting Internet standards and discussions, stored online.
    *   **W3C (World Wide Web Consortium):** Develops protocols and guidelines for the Web (e.g., HTML, Web privacy).

**1.7 Metric Units**
The book uses metric units (e.g., kbps, Mbps, Gbps, Tbps for 10^3, 10^6, 10^9, and 10^12 bits/sec, respectively) and specific abbreviations for bytes (KB, MB, GB, TB for 2^10, 2^20, 2^30, and 2^40 bytes, respectively) to avoid ambiguity, as these are not always powers of two.

**1.8 Outline of the Rest of the Book**
The book follows the hybrid five-layer model (Fig. 1-23).
*   **Chapter 2 (Physical Layer):** Theoretical basis for data communication, transmission media, digital modulation, multiplexing, and examples like the public switched telephone network and mobile telephone system.
*   **Chapters 3 & 4 (Data Link Layer):**
    *   **Chapter 3:** Sending packets across a link, error detection/correction, flow control, and data link protocols like Packet over SONET and ADSL.
    *   **Chapter 4 (Medium Access Sublayer):** Sharing a channel among multiple computers, including wireless (802.11, RFID) and wired LANs (Ethernet), and LAN switches.
*   **Chapter 5 (Network Layer):** Routing algorithms, congestion control, internetworking, and the Internet's network layer (IP, OSPF, BGP).
*   **Chapter 6 (Transport Layer):** Connection-oriented protocols, reliability, TCP and UDP, and performance issues.
*   **Chapter 7 (Application Layer):** DNS, email, the Web, streaming media, and content delivery networks.
*   **Chapter 8 (Network Security):** Cryptography, communication security (IPsec, firewalls, VPNs, wireless security), authentication protocols, email security (PGP, S/MIME), Web security (SSL), and social issues (privacy, freedom of speech, copyright).
*   **Chapter 9 (Reading List and Bibliography):** Suggestions for further reading and a comprehensive bibliography.

**1.9 Summary**
Chapter 1 summarizes the pervasive uses of computer networks for businesses and individuals, the increasing role of wireless and embedded devices, and the associated social issues. It introduces network types by scale, the layered approach to network software, and the foundational OSI and TCP/IP reference models, before presenting the book's hybrid five-layer model. It also previews key examples like the Internet, mobile phone networks, and wireless LANs, highlighting the importance of standardization and defining metric units used throughout the text.