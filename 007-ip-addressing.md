# IP Addressing

## Outline

- IP Addresses Overview
- Address Classes
  - Class A
  - Class B
  - Class C
  - Class D
  - Class E
  - CIDR
- Special Address

  - Loopback address
  - Local broadcast address

- Network Masks

---

## What is an IP Address?

- layer 3 logical address assigned by an administrator
  - MAC Addresses - built in to NIC
- resides at Layer 3 of OSI Model
- used to identify specific devices on a network
- every device on the internet has a unique IP address

RFC1918 Addresses

- 10.1.1.1

---

### IPv4

- Layer 3 or network layer protocol
- Connection-less Protocol (no sessions)
  - TCP is connection oriented
  - 3 way handshake
  - SYN / SYN Ack / ACK from Transmitter to Receiver
  - ability to retransmit missing packets (UDP doesn't)
- packets treated independently
  - may take different paths
  - Load balancing
  - Bandwidth - OSPF
  - hopcount - RIP (Routing protocols determine the best route)
- hierarchical addressing structure
  - Network and Host portion
- best effort delivery

- no data recovery features
- no built in session
- no retransmission

**TCP**

- handle dropped corrupted and misdirected packets

---

### Format Overview

- 32bit (10.1.1.1)
- x.x.x.x (each x 8 bits - octet)
- has a hierarchical structure to enable routing
- network portion
- host portion
- for routing like DHL or FexEx routing parcel based on an address
- routers route traffic to destination address in the packet

**IP Address**

- Network Address Portion (Network ID)

  - identifies a specific network
  - routers maintain routing tables that contain the network
  - look at destination of IP address and match to network address

- Host Address Portion (host ID)
  - identifies a specific endpoint on a network
  - server, printer, PC, iphone, ipad etc

---

## Address Classes

- 1981 until introduction of classes in Domain routing in 1993
- divide IPv4 into 5 address classes

Class A, Class B, Class C => Unicast traffic

- Accommodate different sizes of networks
- Aids in classifying networks
- support 60 million IP addresses, replaced by CIDR
- determined by the Internet Assigned Numbers Authority (IANA)

Class D => multicast

Class E => reserved for future or experimental purposes

- IPv6: does not use address classes
- IPv4: address classes was replaced by CIDR in 1993

### Class A

- first 8 bits: network, last 24 bits: host
- start with a **binary 0**
- Binary Range **0.0.0.0 to 127.255.255.255**
- Exception
  - 127 is reserved for loopback
  - 0 network is reserved for default network
- Actual Range: 1.0.0.0 to 126.255.255.255

### Class B

- first 16 bits: network, last 16 bits host
- starts with **binary 10**
- Binary range: **128.0.0.0 to 191.255.255.255**

### Class C

- first 24 bits: network
- starts with **binary 110**, last 8 bits host
- Binary range **192.0.0.0 to 223.255.255.255**

### Class D

Class A, B, C = Unicast

Class D = Multicast

Is talking to a group of devices rather than 1 to 1 communication.

- multicast
- starts with **binary 1110**
- Binary range 224.0.0.0 to 239.255.255.255

### Class E

- starts with **binary 1111**
- Binary range 240.0.0.0 to 255.255.255.255 (reserved for broadcast)

---

### Class A Network Address

Class A = 8 bits network

- 10.0.0.0 = Network Address
- 10.1.2.3 = Host Address
- Class A Networks 1 to 126

Two hosts can have the same network portion

---

### Class B Network Address

- 172.16.0.0 = Network Address
- 172.16.1.2 = Host Address
- Class B Networks 128 to 191

---

### Class C Network Address

- 192.168.1.0 = Network Address
- 192.168.1.1 = Host Address
- Class C network 192 to 223

---

## Special Addresses

### Directed Broadcast Address

- host sends data to all devices on a specific network
- binary 1s in the entire host portion of the address

Network 172.31.0.0

- directed broadcast = 172.31.255.255

Routers can route directed broadcast

- disabled by default

  - hacking utilities that you can download
  - Denial of Service Attacks - SMURF

#### Example

172.16.0.1 (Network 172.16.0.0)

-> Step 1: Directed broadcast to 172.31.255.255

-> Router

-> Network 172.31.0.0

-> All hosts (172.31.0.1)

- receive
- accept
- forward to higher level protocols for processing

---

### Local Broadcast Address

- communicate with all devices on local network
- address is all binary 1s
  - 11111111.11111111.11111111.11111111
  - 255.255.255.255

#### Example

- host request an IP address from DHCP server

Host (No IP Address) -> broadcast -> DHCP Server

- DHCP: Dynamic Host Configuration Protocol, provides IP addresses dynamically to devices such as PCs, phones, iPads, IP Telephones.

- always dropped by routers and layer-3 switches (255.255.255.255)
  - can be override with DHCP forwarding or DHCP relay

---

### Local Loopback Address

- used to let a system send a message to itself for testing
- this is very useful to make sure that the TCP/IP stack is correctly installed on a machine
- **127**.0.0.1
  - Class A Address
  - 16 Million Addresses

#### IPv6

- ::1 (loopback address)

**Note**

- routers have loopback addresses, which are not the same as the local loopback address (**Routers Loopback Address** !== Local Loopback Address)
- router or switch may have a Loopback Interface (10.1.1.1/32 vs 127.0.0.1)

---

### Private Addresses

**RFC** - Request for Comments (IETF)

- Internet Standards
- RFV1149 - IP over Avian Carriers (humor)

#### RFC1918

- Private IP addresses
- non routable on the Internet

the exhaustion of IPv4 has postponed for longer

Three blocks of IP addresses

- 1 Class A Network
  - 10.0.0.0 to 10.255.255.255
- 16 Class B Networks
  - 172.16.0.0 to 172.31.255.255
- 256 Class C Networks
  - 192.168.0.0 to 192.168.255.255

> Will not be accepted by Internet Service Provides (not routed on Internet)

> When sending traffic from an internal address e.g. 10.1.1.1 to google.com, **this IP has to be NATed** (Network Address Translated) **to a public IP address** such as 15.1.1.1.

#### IPv4 Link - Local Addresses

- RFC3927
  - Automatic Private IP Address (APIPA, Microsoft)

This is for when a PC is configured for DHCP

- when no DHCP server is available
- - range 169.254.0.0/16
- allow two computers to communicate when there are no DHCP servers available
- can immediately communicate without configuration
- host randomly generate the host specific part of the address

the PC automatically chooses an IP address

Hosts communicate on the local link but their traffic is not routable

---
