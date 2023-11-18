# IP Addressing

## Outline

- IP Addresses Overview
- Address Classes
  - Class A - E
  - CIDR
- Special Address

  - loopback address
  - local broadcast address

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
- Binary Range 0.0.0.0 to 127.255.255.255
- Exception
  - 127 is reserved for loopback
  - 0 network is reserved for default network
- Actual Range: 1.0.0.0 to 126.255.255.255

### Class B

- first 16 bits: network, last 16 bits host
- starts with **binary 10**
- Binary range: 128.0.0.0 to 191.255.255.255

### Class C

- first 24 bits: network
- starts with **binary 110**, last 8 bits host
- Binary range 192.0.0.0 to 223.255.255.255

### Class D

Class A, B,C = Unicast

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
