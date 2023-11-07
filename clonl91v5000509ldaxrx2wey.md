---
title: "🌐🔌 DevOps 4.0: Networking Magic 💼🚀"
seoTitle: "🌐🔌 DevOps 4.0: Networking Magic 💼🚀"
seoDescription: ""Building Bridges: Navigating the World of Networking in DevOps""
datePublished: Tue Nov 07 2023 00:23:58 GMT+0000 (Coordinated Universal Time)
cuid: clonl91v5000509ldaxrx2wey
slug: devops-40-networking-magic
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1699291751967/e0dfe9cb-bd0c-4775-9809-e0e804eceeb5.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1699316613867/a2a73db3-7ca8-4e7e-8ceb-7c1c5f74c35d.jpeg
tags: linux, developer, devops, networking, wemakedevs

---

# Contents in this series:

1. Components
    
2. OSI Model
    
3. Classification
    
4. Devices
    
5. Home Network
    
6. IP Addresses
    
7. Protocols
    
8. DNS & DHCP
    
9. Network Commands
    

# What is a Computer Network ?

A computer network is ***a group of interconnected nodes or computing devices that exchange data and resources with*** each other.

# Components of a Computer Network -

1. Two or more Computers/Devices.
    
2. Cables as links between the computers.
    
3. A network interfacing card(NIC) on each.
    
4. Computer
    
5. Switches to connect multiple interaces to each other.
    
6. Routers to connect multiple networks.
    
7. Software called Operating System.
    

# OSI Model:

The Open Systems Interconnection model is a conceptual model from the International Organization for Standardization that "provides a common basis for the coordination of standards development for the purpose of systems interconnection."

* The basic elements of a layered model are:
    
    * **Services** - A service is a set of actions that a layer offers to another (higher) layer.
        
    * **Protocol** - A protocol is a set of rules that a layer uses to exchange information.
        
    * **Interface** - A interface is communication between the layers.
        

## Sending - Receiving Letters:

The OSI model, often considered the backbone of network communication, can be beautifully explained by drawing parallels to sending and receiving letters.

**Layer 7: Application Layer - Writing the Letter**

This is the layer where the action begins. Here, the sender sits down to write the letter. It's where the content is created, and the sender understands how to craft a meaningful message.

**Layer 6: Presentation Layer - Putting It in an Envelope**

After crafting the letter, the sender carefully places it in an envelope. The Presentation Layer is like this envelope; it formats and encodes the message. The sender understands what's happening, just as one knows how to seal an envelope.

**Layer 5: Session Layer - Dropping it into the Mailbox**

The sender drops the sealed letter into a mailbox, which marks the transition to the Session Layer. This layer manages the communication session between the sender and the mailbox. The sender may not fully understand it but knows the letter is sent.

**Layer 4: Transport Layer - Letter's Journey to the Post Office**

The letter's journey from the mailbox to the post office is akin to the Transport Layer. The sender is unaware of these inner workings. It ensures the letter's safe travel, similar to how this layer manages data integrity and flow control.

**Layer 3: Network Layer - Delivery to the Receiver's Post Office**

Now the letter arrives at the receiver's post office. Just as the sender didn't comprehend the post office's operation, it's here the letter is passed to the receiver's network - the Network Layer. It determines the best path for the letter.

**Layer 2: Data Link Layer - In the Receiver's Mailbox**

The letter reaches the receiver's mailbox. The Data Link Layer, like the mailbox, receives and sends data frames. The sender and receiver remain blissfully unaware of these low-level details.

**Layer 1: Physical Layer - Picking up and Reading the Letter**

The receiver picks up the letter, takes it inside, and opens it. The Physical Layer is like the receiver's hands in this analogy. It ensures the actual, physical transmission of data. Both the sender and receiver don't concern themselves with this layer.

Just as the sender's main focus is writing and sending, and the receiver's priority is receiving and reading the letter, the OSI model lets computers and networks manage the complexities in between. It ensures that data gets from one point to another, regardless of the technology and systems involved, leaving users to focus on their own tasks.

### All the layers in detail:

**1\. Physical Layer**

* Hardware layer.
    
* Deals with the physical connection between devices.
    
* Concerned with transmitting raw bits over a physical medium.
    
* Examples: Cables, switches, network adapters.
    

**2\. Data Link Layer**

* Responsible for reliable data transfer(frames) between two directly connected nodes.
    
* Divided into two sub-layers: Logical Link Control (LLC) and Media Access Control (MAC).
    
* Manages error detection and correction.
    
* Examples: Ethernet, Wi-Fi (802.11), PPP.
    

**3\. Network Layer**

* Focuses on routing data packets from the source to the destination across multiple networks.
    
* Determines the best path for data, taking into account network topology and congestion.
    
* The Internet Protocol (IP) is a fundamental part of this layer.
    
* Examples: IPv4, IPv6, routing protocols (OSPF, BGP).
    

**4\. Transport Layer**

* Ensures end-to-end communication between the sender and receiver.
    
* Responsible for data segmentation, error checking, and flow control.
    
* Manages connections (TCP) or sends data without connection setup (UDP).
    
* Examples: TCP, UDP, SCTP.
    

**5\. Session Layer**

* Manages sessions (connections) between applications.
    
* Handles session establishment, maintenance, and termination.
    
* Coordinates data exchange and error recovery.
    
* Examples: NetBIOS, RPC, PPTP.
    

**6\. Presentation Layer**

* Focuses on data translation and encryption.
    
* Ensures data is presented in a readable format for the application layer.
    
* Handles data compression, encryption, and character encoding.
    
* Examples: SSL/TLS, ASCII, JPEG, MPEG.
    

**7\. Application Layer**

* The topmost layer, directly interacting with end-user applications.
    
* Provides a platform-independent interface for the application.
    
* Houses application-specific protocols.
    
* Examples: HTTP, FTP, SMTP, DNS.
    

## Classification of Network by Geography:

1. **Local Area Network (LAN):**
    
    * **Scope:** LANs are confined to a relatively small geographic area, such as a single building, office, or campus.
        
    * **Size:** They typically cover a small area, often no more than a few kilometers in diameter.
        
    * **Ownership:** LANs are often owned, set up, and maintained by a single organization.
        
    * **Examples:** Home networks, office networks, university campus networks.
        
2. **Metropolitan Area Network (MAN):**
    
    * **Scope:** MANs cover a larger geographic area than LANs but are smaller than WANs.
        
    * **Size:** They can extend across a city or a metropolitan area.
        
    * **Ownership:** MANs can be owned by a single organization, a consortium of organizations, or a service provider.
        
    * **Examples:** City-wide networks used for connecting multiple campuses of a university, cable TV networks, and municipal area networks.
        
3. **Wide Area Network (WAN):**
    
    * **Scope:** WANs cover a large geographic area, often a country, continent, or even globally.
        
    * **Size:** They can span very long distances, relying on various technologies like leased lines, satellites, or undersea cables.
        
    * **Ownership:** WANs can be public or private, and they often involve multiple service providers.
        
    * **Examples:** The internet, global corporate networks, intercontinental communication links.
        

## Devices:

1. **Physical Layer (Layer 1):**
    
    * **Hub:** At the physical layer, hubs operate. They are responsible for basic signal forwarding without any intelligence.
        
    * **Repeater:** Repeaters are used to extend the range of a network by regenerating signals.
        
2. **Data Link Layer (Layer 2):**
    
    * **Switch:** Switches operate at the data link layer and use MAC addresses to forward data frames within a LAN. (Intelligent)
        
    * **Bridge:** Bridges are used to segment and filter traffic in a LAN.
        
3. **Network Layer (Layer 3):**
    
    * **Router:** Routers operate at the network layer and are responsible for forwarding data between different networks. They make decisions based on IP addresses.
        
    * **Layer 3 Switch:** Some high-end switches have routing capabilities and operate at both Layer 2 and Layer 3.
        
4. **Transport Layer (Layer 4):**
    
    * **Firewall:** Firewalls operate at the transport layer and can filter traffic based on port numbers, IP addresses, and more. They enforce security policies.
        
    * **Load Balancer:** Load balancers distribute network traffic across multiple servers to ensure availability and optimize resource utilization.
        
5. **Session, Presentation, and Application Layers (Layers 5-7):**
    
    * **Gateway:** Gateways operate at these upper layers and perform protocol translation and data format conversion. They connect different types of networks, like LANs and the internet.
        
6. **End-User Devices:**
    
    * **Computers, Smartphones, Tablets:** These devices operate at the application layer and interact directly with users. They run applications, web browsers, and other software to access network resources.
        
    * **Printers, Scanners, Cameras:** Peripheral devices connect to the network for printing, scanning, and transferring data.
        
    * **IoT Devices:** Various Internet of Things (IoT) devices, such as smart thermostats, sensors, and cameras, can connect to the network to transmit data.
        

### IPv4:

**IPv4 (Internet Protocol version 4):** IPv4 is the fourth version of the Internet Protocol, which is used to identify and locate devices on a network, including the internet. It is a numerical addressing system and the most widely used version. An IPv4 address consists of a 32-bit binary number, typically represented in human-readable form as a series of four decimal numbers separated by periods (e.g., 192.168.0.1).

**Public IP Address:**

* **Definition:** A public IP address is an address assigned to a device or network by an Internet Service Provider (ISP) to enable it to communicate over the internet. It is a globally unique and routable address.
    
* **Range:** Public IP addresses are typically assigned from specific IP address ranges reserved for the public internet. These ranges include Class A, B, and C networks, and they are publicly registered and maintained by regional internet authorities.
    
* **Example:** An example of a public IP address is 203.0.113.15.
    

**Private IP Address:**

* **Definition:** A private IP address is an address assigned to devices within a private network, such as a home or office network. These addresses are not globally routable on the public internet, meaning they are used for local communication within a specific network.
    
* **Range:** Private IP addresses are typically assigned from specific address ranges reserved for private networks. The most commonly used private IP address ranges are defined in RFC 1918 and include:
    
    * **Class A:** 10.0.0.0 to 10.255.255.255
        
    * **Class B:** 172.16.0.0 to 172.31.255.255
        
    * **Class C:** 192.168.0.0 to 192.168.255.255
        
* **Example:** Examples of private IP addresses are 192.168.1.100, 10.0.0.1, or 172.16.0.5.
    

### Protocols:

A protocol, in the context of computer science and networking, is a set of rules and conventions that define how data is transmitted and received over a network or between computing systems.

| Characteristic | TCP | UDP |
| --- | --- | --- |
| **Full Name** | Transmission Control Protocol | User Datagram Protocol |
| **Connection** | Connection-oriented | Connectionless |
| **Reliability** | Reliable (guaranteed delivery, in-order data) | Unreliable (no guarantees) |
| **Handshake** | Three-way handshake | No handshake |
| **Order of Data** | Guaranteed order of data delivery | No guarantee of order |
| **Acknowledgments** | Uses acknowledgments (ACKs) | No acknowledgments |
| **Flow Control** | Uses flow control mechanisms | No flow control |
| **Error Detection and Handling** | Detects and retransmits lost or corrupted data | No error handling |
| **Header Size** | Larger header size | Smaller header size |
| **Use Cases** | Web browsing, email, file transfer, reliable data transfer | Streaming, video conferencing, real-time gaming, scenarios where minor data loss is acceptable |
| **Examples of Protocols** | HTTP, HTTPS, FTP, SMTP, SSH, Telnet | DNS, DHCP, VoIP, online gaming |

### Protocol and Port Numbers:

| Protocol | Port Number | Description |
| --- | --- | --- |
| HTTP | 80 | Hypertext Transfer Protocol |
| HTTPS | 443 | HTTP over TLS/SSL (Secure Sockets Layer) |
| FTP | 21 | File Transfer Protocol |
| SSH | 22 | Secure Shell (used for secure remote access) |
| Telnet | 23 | Telnet remote login service |
| SMTP | 25 | Simple Mail Transfer Protocol |
| DNS | 53 | Domain Name System |
| HTTP Proxy | 3128 | HTTP Proxy |
| POP3 | 110 | Post Office Protocol (used for email retrieval) |
| IMAP | 143 | Internet Message Access Protocol (used for email retrieval) |
| HTTPS (Alt) | 8443 | HTTPS alternate (common for Tomcat) |
| RDP | 3389 | Remote Desktop Protocol (used for remote desktop access) |
| FTP Data | 20 | FTP data transfer |
| SNMP | 161 | Simple Network Management Protocol |
| SNMP Trap | 162 | SNMP Trap (used for network monitoring) |
| MySQL | 3306 | MySQL database system |
| PostgreSQL | 5432 | PostgreSQL database system |

### OSI vs TCP/IP:

| Layer | OSI Model | TCP/IP Model |
| --- | --- | --- |
| 7 | Application (User Interface) | Application (User Interface) |
| 6 | Presentation (Data Translation) |  |
| 5 | Session (Session Management) |  |
| 4 | Transport (End-to-End Communication) | Transport (End-to-End Communication) |
| 3 | Network (Routing) | Internet (Logical Addressing and Routing) |
| 2 | Data Link (MAC and LLC) | Network Access (Data Link and Physical) |
| 1 | Physical (Hardware) |  |

### Networking Commands:

`ifconfig` or `ip addr show` - The `ifconfig` command, which stands for "interface configuration," is a command-line utility used to configure and display information about network interfaces on a Unix or Linux-based system. It provides detailed information about network interfaces, including their IP addresses, netmasks, MAC (Media Access Control) addresses, and more.

`ping 192.168.1.1` - The `ping` command is used to send ICMP (Internet Control Message Protocol) echo requests to a destination host or IP address. When you run `ping` followed by an IP address, it sends a series of echo requests to that IP address and waits for echo replies. This is often used to check if a host is reachable and measure the round-trip time (latency) for packets to reach the destination and return.

`tracert www.google.com or traceroute www.google.com` - The `traceroute` command is used to trace the route that packets take from your computer to a destination IP address or hostname, showing each hop (router) along the way.

`netstat antp` - It will display a list of all TCP connections, both listening and non-listening, showing the numeric addresses, and providing information about the program and its PID that's associated with each socket.

`nmap` (Network Mapper) is a powerful open-source tool used for network discovery and security auditing. It allows you to discover hosts and services on a computer network, find open ports, identify the operating systems of networked devices, and more.

`dig` command is a network administration tool used for querying DNS (Domain Name System) servers. When you run `dig` [`www.google.com`](http://www.google.com), you are asking your system to retrieve DNS information about the domain "[www.google.com](http://www.google.com)". `nslookup` is similar.

`route` command is used to display or manipulate the IP routing table in Unix-like operating systems. When you run `route -h`, it typically displays a brief help message with information about how to use the `route` command and its various options. This help message provides a quick reference for the command's syntax and options.

`arp` - The `arp` command in Linux is used to display and manage the ARP (Address Resolution Protocol) cache, which is a table that maps IP addresses to MAC (Media Access Control) addresses on a local network. It can help you view, add, or delete entries in the ARP cache. The ARP cache is used to determine the MAC address associated with a specific IP address on the local network.

`mtr` - It stands for "My Traceroute," and it's a network diagnostic tool that combines the functionality of both the `traceroute` and `ping` commands.

`telnet` The command `telnet 192.168.56.25 3306` is attempting to establish a Telnet connection to the host with the IP address 192.168.56.25 on port 3306.

# Conclusion:

In this blog, we've explored the fascinating world of networking, understanding how data flows between devices, the significance of protocols and port numbers, and various networking commands. We hope this knowledge empowers you to navigate the digital landscape with confidence.

But our exploration doesn't stop here! Stay tuned for our upcoming blog, where we'll delve into the exciting realm of containers. Discover how these efficient, isolated environments are revolutionizing software development and deployment. Don't miss it!