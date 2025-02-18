# TCP/IP Stack Project

## Overview
This project involved the collaborative development of a functional **TCP/IP stack**, a key component in networking, that enables reliable byte stream communication between clients and servers. The focus of the project was to design and implement the core protocols that form the backbone of modern networking, specifically the **Transmission Control Protocol (TCP)** and **Internet Protocol (IP)**. The project was developed with a focus on achieving reliable communication and efficient network routing.

## Project Components

### 1. **Reliable Byte Stream**:
   - The primary goal of this part of the project was to implement TCP’s reliable byte stream functionality.
   - We created a mechanism that ensures data sent between a client and server is received in the correct order and without errors.
   - This was done by implementing various mechanisms like **sequence numbers**, **ACKs (Acknowledgments)**, **timeouts**, and **retransmissions** to guarantee reliability over potentially unreliable networks.

### 2. **Connection Establishment**:
   - The project involved the design and implementation of the **three-way handshake** for establishing a TCP connection.
   - The handshake was implemented as follows:
     1. **SYN**: The client sends a synchronization request.
     2. **SYN-ACK**: The server responds with an acknowledgment, agreeing to the connection.
     3. **ACK**: The client finalizes the handshake and starts the data transfer.
   - This mechanism ensures both parties are ready for communication before data is exchanged.

### 3. **Network Routing**:
   - The **IP layer** was responsible for routing data packets across different networks.
   - We implemented basic packet forwarding, including the ability to handle **IP addresses**, **subnetting**, and **routing tables**.
   - A routing table was maintained that mapped destination IPs to their respective network interfaces.

### 4. **Packet Formatting and Parsing**:
   - In order to transmit data across the network, we needed to ensure proper packet formatting at both the IP and TCP layers.
   - The project involved creating functions to **format** and **parse** packets according to the IP and TCP headers, which included the proper fields for each protocol (e.g., source/destination ports for TCP, source/destination IPs for IP).
   - We also implemented **checksums** to detect errors in packet transmission.

### 5. **Client-Server Communication**:
   - To demonstrate the stack’s functionality, we developed both **client** and **server** programs.
   - The client sends a request (e.g., a message) to the server, and the server responds after processing the request.
   - This two-way communication was essential for demonstrating the stack's ability to handle reliable data transfer over the network.

### 6. **Error Handling**:
   - Implemented **error recovery** mechanisms, ensuring the system could recover from packet loss, delayed ACKs, and other transmission errors.
   - The TCP layer was responsible for ensuring that lost packets were retransmitted, and that out-of-order packets were handled properly.

## Key Technologies Used
- **C Programming Language**: The entire stack was developed using C, allowing low-level manipulation of memory and network interfaces.
- **Networking Concepts**: Implemented fundamental networking concepts such as **sockets**, **IP routing**, **TCP connections**, and **packet parsing**.
- **Data Structures**: Utilized data structures like **linked lists** and **queues** for managing connection states, packet buffers, and routing tables.

## Challenges Encountered
- **Reliability of Data Transfer**: Ensuring that data was reliably transmitted and received across different networks was a key challenge. Implementing retransmissions and proper acknowledgment mechanisms required careful handling of timers and sequence numbers.
- **Routing Efficiency**: Developing an efficient routing table for IP addressing and ensuring correct packet forwarding involved managing various edge cases, such as incorrect routes and unreachable destinations.
- **Packet Loss and Retransmissions**: Handling packet loss in a real-world network scenario required the implementation of retransmission mechanisms and proper sequencing of packets.

## Results
- A fully functioning TCP/IP stack that supports basic client-server communication over a network.
- Demonstrated the ability to reliably transfer data between two machines, with handling for out-of-order packets, retransmissions, and error detection.
- A solid understanding of how the TCP and IP protocols work together to ensure reliable communication over potentially unreliable networks.

