# ECE358

# Internet

## The network edge
* end system(web email)
* client/server model(web browser)
* peer-peer model (skype)

### How to connect an end system to an edge router
        WiFi, Ethernet, DSL(Digital Subscriber Line)
### DSL
        Use existing telephone infrastructure
        UP: 1Mbps (today < 256kbps)
        Down: 8Mbps(today < 1 Mbps)
### Ethernet Internet 
        Use in companies and universities
        Speed vary from 10Mbps -> 10Gbps
### WiFi
        Shared wireless access network connects end system to router
        Speed 11Mbps -> 1Gbps
        
## The Network Core
### Question how is data transferred through net
1. Circuit switching: dedicated circuit per call telephone net
2. Packet-switching: data sent through the net in discrete chunks


### Circuit Switching
End-end resources are reserved for call/session

* call setup required
* dedicated resources: no sharing
* link bandwidth, switch capacity 
* circuit like performace

Network resources are divided into piece, resources piece remain idle if not used by owning call

__Sample Question__

How long does it take to send a file of 640,000 bits from host A to host B over circuit-switched network

Assume:  link speeds = 1.536Mbps.  each link uses TDM with 24 slots/sec. a user received one slot every 8 slots in the TDM. It takes 500msec to establish an end to end circuit

Answer:  24slots = 1.536Mbps  one slots = 64000bits 

A user got 3 slots in one sec = 24/8 = 3 * 64000bits

Time needed = total/3*64000 = 3.33

3.33+0.5 = 3.83

### Packet switching

* UserA, B packet share network resources
* each packet uses full link bandwidth
* resources are used are needed
* store and forward: packets move one hop at a time (entire packet must arrive at router before it can be transmitted on next link)


### Packet switching vs circuit switching

- Packet switching allow more users to use networ
- Great for bursty data: you can suppot more users
- Excessive congestion: packet delay and loss
- always using the network
- but performance is not guarantee

## How do loss and delay occur
- packet arrival rate to link exceeds output link capacity
- packets queue, wait for turn
- packet will dropped if no free buffers

## Why layering
- Very different functionalities are addressed in different layers
- Modularization facilitates better maintenance and system evolution

## Link Layer

### Where is link layer implemented?

- in each and every host and router
- link layer implemented in adapter
- attaches into host's system buses
- combination of hardware, software, firmware

### Error Detection: Cyclic Redundancy Check
- view data bits, D, as a binary number
- choose r+1 bit pattern(generator), G
- __goal__: compute r CRC bits, R, such that 
    - <D,R> is exactly divisible by G
    - receiver knows G: Divides <D,R> by G. If non-zero remainder: error detected
- can detect all burst errors less than r+1 bits
- widely used by Wifi ethernet

## Multiple Access Links and Protocols

### Two types of Links

- point to point i.e. ppp
- broadcast i.e. LAN

### Multiple Access protocols
- single shared broadcast channel
- two or more simultaneous transmissions cause collision
- multiple access protocol
    - distributed algorithm that determines when a node can transmit
        
            Packet collision occurs at the receiver, but transmitters must know that collision has occurred

### Ideal multiple access protocol

1. When one node wants to transmit, it can send at rate R
2. When M nodes want to transmit, each can send at average rate R/M
3. Full decentralized
    - no special node to coordinate transmissions
    - no synchronization of clocks and time slots
4. Simple i.e. no complex hardware

### MAC Protocols: a taxonomy
- channel Partitioning example in cellular networks
    - divide channel into smaller "pieces"
        - Time Division Multiple Access
        - Frequency Division Multiple Access
### Random Access
- channel not divided; allow collisions
- "recover" from collisions __OR__ do not let collisions happen

- Taking turns
    - nodes take turns to transmit

### Random Access Protocols

- When a node has a packet to send
- two or more transmitting nodes -> "collision"
- random access MAC protocols specify
    - how to detect 
