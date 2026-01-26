---
title: "networking-fundamentals"
date: 2026-01-23
tags: ["linux","networking"]
---

*Date: 2026-01-23*
{{< tags >}}

## Intro
## The OSI (Open Systems Interconnection) Model
- The osi model is a conceptual framework that describes seven distinct layers of network communication. It  helps us to understand how different technologies work together to enable a network.
- Its basically a set of rules that explains how different computer systems communicate over a network.
- It consists of 7 layers and each layer has specific functions and responsibilities
### Layer 1 : Physical Layer

- The lowest layer of the OSI model
- Responsible for the actual physical connection between devices
- Contains information in the form of bits and transmits them from one node to the next (0s and 1s)
- When receiving data, this layer will get the signal received and convert it to 0s and 1s and send them to the DLL
- Common physical layer devices are hub, repeater and cables
- Physical layer specifies how the different devices are arranged in a network i.e. bus topology, star topology or mesh topology
- This layer also defines how the data flows between two connected devices e.g simples, half duplex and full duplex
### Layer 2 : Data Link Layer (DLL)

- Responsible for the node to node delivery of the message
- The main function is to make sure data transfer is error-free from one node to another over the physical layer
- When a packet arrives in a network, it is the responsiblity of the DLL to transmit it to the host using its MAC address.
- Switches and bridges are the common DLL devices
-  Packet in the DLL is referred to as Frame
- DLL also encapsulates the sender's and receiver's MAC address in the header 
### Layer 3 : Network Layer

- The network layer is responsible for the transmission of data from one host to the other located in different networks. 
- It also takes care of packet routing i.e. selection of the shortest path to transmit the packet from the number of routes available
- The sender's and receiver's IP address are placed in the header by the network layer
- Network layer is implemented by networking devices such as routers and switches
- Protocols - IP(Internet Protocol), ICMP (Internet Control Message Protocol)
### Layer 4 : Transport Layer
- It is responsible for the end to end delivery of the complete message (reliability of communication) through flow-control and error control
- Data from session layer is divided into units called segments. Each segment has a port number and sequence number.
- Port number is used to direct each segment to the correct application/service
- Sequence number is used to arrange the segments into the correct order to form a correct message at the receiver.
- Transport layer helps in flow-control i.e it helps in controlling the amount of data being transmitted.
- Transport layer also helps in error-control i.e if some data fails to reach the destination, transport layer uses Automatic Repeat Request schemes to retransmit the lost or corrupted data.
- It also adds source and destination port number in its header
- Protocols - TCP (Transmission Control Protocol)(connection-oriented transmission), UDP (User Datagram Protocol)(connectionless transmission)
### Layer 5 : Session Layer
- This layer is responsible for the establishment of connections, management of connections, termination of sessions between 2 devices. It also provides authentication and security
### Layer 6 : Presentation Layer
- Also called the translation layer. The data from the application layer is extracted here and manipulated as per the required format to transmit over the network.
- After translation, data can be compressed so that it is transmitted effectively
- After compression, data is encrypted for security.
- Protocols used here are TLS/SSL for encryption.
### Layer 7 : Application Layer
- Provides the interface for applications to access network services.
- Protocols: HTTP, HTTPS, FTP, SMTP, DNS

### Analogy
- Step 1: Person A interacts with e-mail application like Gmail, outlook, etc. Writes his email to send. (This happens at Application Layer).
- Step 2: At Presentation Layer,Mail application prepares for data transmission like encrypting data and formatting it for transmission.
- Step 3: At Session Layer there is a connection established between the sender and receiver on the internet.
- Step 4: At Transport Layer, Email data is broken into smaller segments. It adds sequence number and error-checking information to maintain the reliability of the information.
- Step 5: At Network Layer, addressing of packets is done in order to find the best route for transfer.
- Step 6: At Data Link Layer, data packets are encapsulated into frames, then MAC address is added for local devices and then it checks for error using error detection.
- Step 7: At Physical Layer, Frames are transmitted in the form of electrical/ optical signals over a physical network medium like ethernet cable or WiFi.

### Ports
- These are communication endpoints that allow different services on a device to send and receive data. Each port is associated with a specific service or process.The use of ports helps computers understand what to do with the data they receive.

Suppose Bob transfers an MP3 audio recording to Alice using the File Transfer Protocol (FTP). If Alice's computer passed the MP3 file data to Alice's email application, the email application would not know how to interpret it. But because Bob's file transfer uses the port designated for FTP (port 21), Alice's computer is able to receive and store the file.

| Port Number | Service                                  |
| ----------- | ---------------------------------------- |
| 20          | File Transfer Protocol                   |
| 21          | File Transfer Protocol                   |
| 22          | Secure Shell (SSH) Secure login          |
| 23          | Telnet Remote Login                      |
| 25          | Simple Mail Transfer Protocol (SMTP)     |
| 53          | Domain Name System (DNS) Service         |
| 80          | Hypertext Transfer Protocol (HTTP)       |
| 110         | Post Office Protocol(POP3)               |
| 123         | Network Time Protocol (NTP)              |
| 143         | Internet Message Access Protocol(IMAP)   |
| 161         | Simple Network Management Protocol(SNMP) |
| 443         | HTTP Secure(HTTPS)                       |

### Subnetting
- This is the process of dividing a large network into smaller, more manageable subnetworks.
- Every IP address e.g 192.168.1.10 has 2 parts;
1. Network ID
2. Host ID
- The subnet mask is the line that separates them.
- An example : 192.168.1.10/24 
- The IP is 192.168.1.10 while the mask is /24 or 255.255.255.0
- The mask /24 means that the first 24 bits (the first 3 numbers) belong to the network ID; 192.168.1. This means that only devices that have their IP addresses starting with 192.168.1 can talk directly with each other.
- The remaining .10 belong to the host ID. This is the host device.
- If a raspberry Pi is 192.168.1.50, it has the same network ID and it can communicate directly. On the other hand, if a server is 192.168.2.50, it has a different network ID and a router(Gateway) is needed for communication.
- CIDR notation = /24.
- /32(One device) - Only fits 1 IP
- /24(Standard LAN) - 256 IPs but we remove the first(Network ID) and last(broadcast) so it fits 254 devices. The broadcast is the speacial IP address used to send a packet to all of the devices in a particular network segment.
- /16(Huge Network) - fits 65,534 devices
- /0(The Internet) - 0.0.0.0/0
- The larger the number after /, the smaller the network. Every time we increase the number by one, /25 we split the previous number of devices by half 256/2, so /25 wil fit 128 IPs.

### Switches and routers

- A **switch** connects devices that are on the same network. It creates a Local Network (LAN).For example, it lets my laptop communicate with the raspberry PI or my phone to the printer.

- It does not care about IP addresses. It uses MAC addresses to identify devices on the LAN.

- It operates on the data link layer.

- A **Router** connects different networks, a private home network to the public internet.

- It uses IP addresses to operate. For example when browsing through the internet from a laptop.

### Routing

- This is the process of directing data packets from source to destination across a network. They use routing tables and protocols to decide the path for data transmission ensuring efficient and reliable communication between devices.

### How does routing work ?

- Data moves along any network in form of data packets. Each data packet has a header that contains information about the packet's intended destination. As a packet travels to its destination, several routers might route it multiple times. Routers perform this process millions of times each second with other millions of packets.

- When a data packet arrives, the router first checks its address in the routing table, the router then forwards the packet on to the next point in the network.

### types of routing

1. Static routing - A network administrator manually configures and selects network routes.

2. Dynamic routing - Routers create and update routing tables at runtime based on actual network conditions. They attempt to find the fastest path from the source to the destination by using a dynamic routing protocol, which is a set of rules that create, maintain and update the dynamic routing table. Its biggest advantage is that it adapts to changing network conditions e.g. traffic volume, bandwidth and network failure.

### DNS

- A Domain Name System translates domain names into IP addresses which allows browsers to access websites or any other internet resources.

### Working process of DNS

1. User input - A user enters a website address e.g www.archlinux.org into their browser
2. Local cache check - The browser checks its local cache to see if it has looked up the address recently. If it finds the address, it is uses that directly without querying external servers.
3. Hosts file check - This is a file that is stored locally that maps domain names to IP addresses.
4. DNS resolver query - If IP address is not found locally, the computer send a request to a DNS resolver, also known as recursive resolver. It is provided by the ISP or network settings. Its like asking a Librarian about a particular book and the librarian goes to search for the book. It can be google (8.8.8.8) or cloudfare.
5. Root DNS server - The resolver sends the request to a root DNS server. The root server doesn't know exactly the IP address for the domain but knows which Top-Level Domain (TLD) server to query based on the domain's extension e.g. .edu
6. TLD server - The TLD server for lets say .edu directs the resolver to the authoritative DNS server for the domain.
7. Authoritative DNS server - This server holds the actual DNS records for the domain, including the IP address for the website's server. It sends the IP address back to the resolver.
8. Final response - The DNS resolver sends the IP address back to the computer, allowing it to connect to the website's server and loads the page.




## References
- https://www.geeksforgeeks.org/computer-networks/open-systems-interconnection-model-osi/
- https://www.cloudflare.com/en-in/learning/network-layer/what-is-a-computer-port/
- https://aws.amazon.com/what-is/routing/#:~:text=Routing%20is%20the%20process%20of,place%20through%20many%20different%20paths
- https://www.geeksforgeeks.org/computer-networks/domain-name-system-dns-in-application-layer/

