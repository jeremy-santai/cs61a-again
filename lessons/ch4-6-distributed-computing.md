# 4.6 Distributed Computing

Distributed computing involves multiple independent computers coordinating to perform joint computations. These systems communicate through **messages**—information transferred over networks rather than through shared memory.

## 4.6.1 Messages

A message protocol establishes rules for encoding and interpreting byte sequences between computers. "A message protocol is a set of rules for encoding and interpreting messages."

### TCP/IP Protocol Stack

The Internet Protocol (IP) transfers data packets with a maximum size of 65,535 bytes. While IP doesn't guarantee packet order or delivery, the Transmission Control Protocol (TCP) provides reliable, ordered transmission by managing sequence information and requesting retransmission of lost packets.

TCP connection establishment follows a three-step handshake before data transfer begins between two computers.

## 4.6.2 Client/Server Architecture

In this model, a server provides services while multiple clients request and consume them. The architecture enables separation of concerns: servers need not know how responses are used, and clients need not understand service implementation details.

**Web Example**: When accessing a webpage, a browser client first queries a Domain Name Server (DNS) to obtain an IP address, then requests content from the web server using HTTP.

### HTTP Protocol

HTTP GET requests retrieve specific web pages. Servers respond with status codes—200 for success, 404 for missing resources—followed by headers containing metadata and content.

### Limitations

Client/server systems have drawbacks: the server represents a single point of failure, and computational resources become scarce when many clients demand services simultaneously.

## 4.6.3 Peer-to-Peer Systems

These systems distribute labor equally among all participants. Each component contributes processing power and memory, and the system's capacity grows with size.

**Key characteristics**: All computers send and receive data while maintaining network organization to ensure reliable message delivery.

**Applications**: Peer-to-peer architecture suits data transfer and distributed storage. Skype exemplifies this model, using specialized "supernodes" as scaffolding for network maintenance while ordinary computers relay communications through their neighborhoods.


---

## Same Chapter

- [Ch4 1 Introduction](ch4-1-introduction.md)
- [Ch4 2 Implicit Sequences](ch4-2-implicit-sequences.md)
- [Ch4 3 Declarative Programming](ch4-3-declarative-programming.md)
- [Ch4 4 Logic Programming](ch4-4-logic-programming.md)
- [Ch4 5 Unification](ch4-5-unification.md)
- [Ch4 7 Distributed Data Processing](ch4-7-distributed-data-processing.md)
- [Ch4 8 Parallel Computing](ch4-8-parallel-computing.md)
