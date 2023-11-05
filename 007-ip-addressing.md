# IP Addressing

## Outline

- IP Addresses Overview
- Address Classes
  - Class A - E
  - CDR
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

## IP Characteristics and IPv4 Address Format

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

### Format Overview

- 32bit (10.1.1.1)
- x.x.x.x (each x 8 bits - octet)
- has a hierarchical structure to enable routing
- network portion
- host portion
- for routing like DHL or FexEx routing parcel based on an address
- routers route traffic to destination address in the packet

---
