---
modified: 2024-09-04T10:36:21+02:00
tags:
  - mooc
---
## Addresses
1. IP Address: 32bit long, e.G. *192.168.0.0*
2. Subnet-Mask, masks which part is designating the network address and which the computer address, e.G. *255.255.255.128* `128 = 2^7 = 32 - 2^7 available ip addresses for computers. `
3. I need three IPs for Network Destination, Broadcast IP and Gateway Interface

![[IP Addresses|700]]
[IP Subnet Calculator](https://www.calculator.net/ip-subnet-calculator.html)

![[Network Map Scheme|700]]

## IP Routing Table
![[Bildschirmfoto 2024-09-04 um 09.54.11.png]]
1. checks each row from top to bottom until it finds a matching row
2. A matching row is a address belonging to a ip address range (**A** - *165.132.9.1-165.132.9.127*)
3. if a destination address (e.G. *165.132.9.5*) is in the range (of A) it sends the packet to the gateway (*164.132.9.126**)
4. if a ip address is **not** within any range then the last row will be a catch-all rule, as it accepts any destination ip, meaning it will send the package to this row's gateway (e.G. *165.132.15.58*)

## OSI / TCP-IP Layer Models

![[TCP-IP Kurs 2024-09-04 10.17.44.excalidraw|700]]
- OSI has **7 Layers** | TCP/IP has **5 layers** (App, Presentation and Session is  united into one Application Layer)

### Network Operations
= How does the Protocol works

A host wants to send a file to another host
1. **Payload segments** = **Application Date File** is divided based on the **MTU** size of the **IP Packet** and **Ethernet Frame size** 
2. Payload segments + TCP
	1. Both hosts setup a TCP session using a *3 way handshake*
	2. host 1 sends a **syn** package, host 2 replies with a **ack** and a **syn** which host 1 **ack** again
	3. TCP Flow and Error control is only controlled end-to-end between the hosts
3. Payload segments + TCP + IP
	1. IP header includes source and destination IP Address
	2. IPv4 and IPv6 have different IP headers
4. Payload segments + TCP + IP + Eth
	1. Ethernet header and