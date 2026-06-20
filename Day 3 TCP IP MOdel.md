A model let us group related jobs into layers.
- Each layer has a specific role.
- Each layer uses the services of the layer below and provides services to the layer above
Protocols live (mostly) at one layer
- Together they form a stack of protocols that work as a team (the network stack)
- (A protocol is a set of rules that define how data should be communicated between devices over a network.)
Today, almost all real networks use TC/IP model.
![[../assets/Pasted image 20260619094156.png]]
A port is just a number used to identify a process running on a host.
![[../assets/Pasted image 20260619095602.png]]

Layer 1: The Physical layer
- Sends and receives bits as electrical, optic, or radio signals over the medium
- Defines things like cables, connectors, signal levels, and link speeds
- The physical aspects of transmitting data are very complex
- Examples: copper UTP cables, fiber-opic cables, Wi-Fi radios and antennas, network interface cards (NICS).
Layer 2: The Local Network layer
The local Network layer provides hop-to-hop delivery of messages on a local network
- A hop is one step along the path between two devices
- from one router or host, to the next router or host in the path
- Switches don't count; a switch just extends the local network, allowing multiple devices to connect
Protocols at this layer include:
- Ethernet (IEEE 802.3)
- Wi-Fi (IEEE 802.11)
Layer 3: The Internet Layer
- The internet layer provides end-to-end delivery between hosts across multiple networks.
  - Internet = inter-network (between networks)
- Uses IP addresses to identify hosts in the network
- Routers operate mainly at this layer, using the message's destination IP address to forward he message toward is final destination host.
Protocols at this layer include:
- IP (IPv4, IPv6)
- ICMP (Internet Control Message Protocol)
Layer 4: The Transport layer
- The Transport layer provides end-to-end communication between application processes. (Also called 'process-to-process' or 'service-to-service')
- Uses port numbers to identify the processes on each host.
- Runs mainly on he communicating hosts; routers normally operate based on IP (Layer 3), not on Transport-layer information.
Protocols in layer 4 include:
- UDP (User Data-gram Protocol): simple and efficient 
- TCP (Transmission Control Protocol): more robust features beyond basic message addressing
Layer 5: The Application layer
- Defines how application processes format, send, and interpret data.
- Network infrastrucutre devices (routers, switches) don't care about Application-layer details.
  - They only move messages across the network.
  - Only the communicating hosts interpret the data.
Protocols at this layer define message formats and rules for specific tasks, such as:
- Browsing web pages (HTTP/HTTPS)
- Transferring files (FTP, TFTP)
- Sending/receiving email (SMTP, POP3, IMAP)
Encapsulation Process:
![[../assets/Pasted image 20260619115017.png]]
Decapsulation Process: ![[../assets/Pasted image 20260619115302.png]]
In encapsulation, the sending host adds headers, and a trailer to the data to prepare it for transmission over the physical medium.
In decapsulation, the receiving host removes the headers and trailer layer by layer until it gets to the data inside.

At each stage in the encapsulation/decapsulaiton process, thre is a name gien to the message:
- The combination of data and a L4 header is called a segment (TCP) or datagram (UDP)
  - TCP creates segments, UDP creates datagrams.
- The combination of a segment/datagram and a L3 header is called a packet 
- The combination of a packet and a  L2 header/trailer is called a frame.
We use alternative names to describe the message at each stage: protocol data unit (PDU)

The contents of each PDU (everything encapsulated by that layer's header/trailer are called the payload)
- ex: A packet's payload is a segment or datagram
