# Ethernet LAN Switching Part 1
Ethernet involves layer 1 and layer 2 of the OSI Model
<img width="1302" height="723" alt="image" src="https://github.com/user-attachments/assets/86a95ef5-48d7-4387-9b93-625f1a9686db" />
<img width="1302" height="723" alt="image" src="https://github.com/user-attachments/assets/f69ac920-3a7e-4784-8fc7-cc3c26220f42" />

# Local Area Networks (LAN)
- A LAN is a network contained within a relatively small area
- Routers are used to connect seperate LANS
- Switches do not seperate LANS, but adding more switches can be used to expand an existing LAN.
<img width="1302" height="723" alt="image" src="https://github.com/user-attachments/assets/c9dbc85b-ecb7-4d16-84f1-0b8b541d30bf" />

This is what a Ethernet Frame looks like:
<img width="1041" height="583" alt="image" src="https://github.com/user-attachments/assets/27601821-f1a3-42b9-94a6-3afc5f3f60d0" />

They're 5 fields in the Ethernet Header.
The Preamble -- SFD -- Destination -- Source -- Type
- SFD are used for syncrhonization and to allow the receiving device to be prepared to receive the rest of the data in the frame.
- The Destination, is the layer 2 address to which the frame is being sent.
- The Source is the layer 2 address of the device which sent the frame.
- The Type indicate the layer 3 protocol used in the encapsulated packet, which is almost always Internet Protocol, or IP version 4, or IP version 6.
- However sometimes the Type is used to indicate the length of the encapsulated data, depending on the version of the ethernet

The Ethernet trailer only has one field 
- FCS is used by the recieving device to detect any errors that might have occured in transmission.

# Ethernet Frame: Preamble & SFD

The Preamble (7 bytes)
- Length: 7 bytes (56 bits)
- Alternatig 1's and 0's
- 10101010 * 7
- Allows devices to syncrhonize their receiver clocks

SFD (1 byte)
- 'Start Frame Delimiter'
- Length: 1 byte (bits)
- 10101011
- Marks the end of the preamble, and the beginning of the rest of the frame

# Ethernet Frame: Destination & Source

Destination (6 bytes) & Source (6 bytes)
- Indicate the devices sending and receiving the frame
- Consist of te destination and soure 'MAC address'
- MAC = Media Access COntrol
- = 6 byte (48-bit) address of the physical device

# Ethernet Frame: Type / Length

Type or Length field ( 2 bytes)
- 2 byte (16-bit) field
- It can be used to represent either the type of the encapsulated packet, or the length of the encapsulated packet
- A value fo 1500 or less in this field indicates the LENGTH of the encapsulated packet (in bytes)
- A value of 1536 or greater in this field indicate the TYPE of the encaupsulated packet (usually - - IPv4 or IPv6), and the length is determined via other methods.

IPv4 = 0x0800 (hexadecimal)
- (2048) in decimal)
IPv6 = 086DD (hexadeicmal
- (34525 in decimal)

# Ethernet Frame FCS

Frame Check Sequence FCS ( 4 bytes)
- The only field of the Ethernet trailer
- 'Frame Check Sequence'
- 4 bytes (32 bits) in length
- Detects corrupted data by running a 'CRC' algorithm over the received data
- CRC = 'Cyclic Redundancy Check'

The total size of the header + trailer = 26 bytes

# MAC Address

Mac Addresses
- 6-byte (48-bits) physical address assigned to the device when it is made
-  A.K.A 'burned-IN Address' (BIA)
-  Is globally unique
-  The first 3 bytes are the OUI (Organizationally Unique Identifier), which is assigned to the company making the device
-  The last 3 bytes are unique to the device itself
-  Written as 12 hexadecimal characters

# Hexadecimal
<img width="827" height="488" alt="image" src="https://github.com/user-attachments/assets/f391be7c-04f0-4bc1-a3cc-f637743ecb84" />

# MAC Address Table

Unicast Frame:
- A frame destined for a single target

Each Switch stores a Dynamic / Dynamically learned MAC address
Every switch will keep a MAC address table like this, and they fill the MAC address table dynamically by looking at the source MAC addresso of frames it receives.
<img width="368" height="290" alt="image" src="https://github.com/user-attachments/assets/8efbe884-9b11-43fa-a363-4d25c4ade375" />

When a Switch doesn't know the DESTINATION MAC ADDRESS of a frame (UNKNOWN UNICAST FRAME), it is forced to FLOOD the frame - Forward the frame out of ALL it's interfaces, except the one it received the packet from.  

When a KNOWN Unicast Frame is known (MAC Address is recognized by the entry in the MAC ADDRESS TABLE), the frame is FORWARDED like normal.
<img width="1298" height="712" alt="image" src="https://github.com/user-attachments/assets/611ff33d-6846-4546-bdb3-63193bac66eb" />

Dyanmic MAC addresses are removed from The MAC address table after 5 minutes of inactivity
