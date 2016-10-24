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
* circuit like performance

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

- Packet switching allow more users to use network
- Great for bursty data: you can support more users
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
-   single shared broadcast channel
-   two or more simultaneous transmissions cause collision
-   multiple access protocol
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
    - how to detect collisions
    - how to recover from collisions (avoid collision)
- Examples of random access MAC protocols
    - ALOHA and slotted ALOHA

### Aloha Protocol

- Developed in the 1970
- connect terminals with mainframes
- WLAN possible but not used
- Cell phone use the protocol to request a channel from the base stations

Pure aloha

- 当传输点有数据需要传送的时候，它会立即向通讯频道传送。
- 接收点在收到数据后，会ACK传输点。
- 如果接收的数据有错误，接收点会向传输点发送NACK。
- 当网络上的两个传输点同时向频道传输数据的时候，会发生冲突，这种情况下，两个点各自等待一段随机长度的时间后，再次尝试传送。

Shared Transmission Medium
-  A receiver can hear multiple transmitters-  A transmitter can be heard by multiple receivers


#### Advantages
Simple, no synchronization. When frame first arrives transmit immediately 
#### Disadvantage
Collision probability increases

### pure Aloha efficiency

        Throughput of Pure Aloha = Total input rate G * prob of successful packet trans = G * e^-2G

### Slotted ALOHA

- all frames are same size
- nodes are synchronized
- notes start to transmit only slot beginning
- tune us divided untie equal size skits 

### Slotted Aloha efficiency

G * e^-G

### CSMA (Carrier Sense Multiple Access)

*Listen before you transmit*

- If channel is sensed idle, transmit entire frame
- if channel is sensed busy, defer transmission

### CSMA/CD(Collision Detection)

- Tx attempts multiple times
- collisions are detected within a short time
- A colliding transmissions is aborted

#### Collision detection
- easy in wired LAN
- not possible in wireless LAN

### Binary exponential back off (MIDTERM)
In Ethernet networks, the algorithm is commonly used to schedule retransmissions after collisions. The retransmission is delayed by an amount of time derived from the slot time and the number of attempts to retransmit.

After c collisions, a random number of slot times between 0 and 2c − 1 is chosen. For the first collision, each sender will wait 0 or 1 slot times. After the second collision, the senders will wait anywhere from 0 to 3 slot times (inclusive). After the third collision, the senders will wait anywhere from 0 to 7 slot times (inclusive), and so forth. As the number of retransmission attempts increases, the number of possibilities for delay increases exponentially.


### Taking Turns MAC protocols

Polling

- master node invites slave nodes to transmit in tur
- typically used with dumb slave devices
- problem(lately, polling overhead, single point of failure)

Token passing

- control token passed from one node to next sequentially 
- token message
- problem (latency, token overhead, single point of failure)

## Ethernet Frame Structure

- 7 bytes with pattern 10101010 followed by one byte with pattern 10101011 
- used to synchronize receiver, sender clock rates

### MAC address: 6 bytes

- if adapter receives frame with matching destination address, or with broadcast address it passes data inflame to upper layer protocol
- otherwise, adapter discards frame

### CRC: checked at receiver

- if error is detected, frame is dropped

### ARP: Address Resolution Protocol

ARP table is hash table of IP and MAC

- each IP node on LAN has ARP table
- ARO table: IP/MAC address mapping for LAN node
- TTL: time after which address mapping will be forgotten (usually 20min)

### what if A wants to send datagram to B and B's MAC address not in A's table

1. A broadcast ARP query packet that containing B's IP address
2. B receives Arp query, relies to A with B's MAC address
3. A saves IP to MAC address pair in its ARP table until this becomes old
4. ARP is plug and play

### LAN solution

- Hubs
    - no frame buffering
    - no CSMA/CD at hub
    - all nodes connected to hub can collide with one another
    - bits coming in on one link go out on all other links at same rate

- Switch
    - store and forward frame
    - transparent hosts are unaware of presses of switchs
    - examine incoming frame's MAC address
    - plug and play

#### How does switch knows that A is reachable via interface 4
        each switch has a switch table
#### How are entries created and maintained in switch table
        basically self learning

- Switch learns which host can be reached through which interfaces
- When frame received switch learns location of sender and records sender location pair in switch table

Question Fall 2012  Final Exam __check__

## WIFI

### PCF Mode

#### The AP(Access Point)

- Operates as the central controller in the BSS
- decided who transmits and when
- There is no contention for medium access
- Can follow a round d-robin policy to allocate slots

#### This mode

- Leads to waste of bandwidth if a scheduled node has no traffic
- Is based on the idea of polling I.e. taking turns in MAC

### DCF Mode (no need for AP if AP is there AP = ordinary node)

#### An AP

- Need not be used
    - Computers can directly communicate among themselves 
- Is used to provided connectivity to the internet

#### In DCF

- All nodes, including the AP, compete for medium access
- The AP does not operate as a central controller

The ap tells all when to enter the PCF mode and the DCF mode



### Handshake mode 

Frame length >= dotRTSThreashold

### Without handshake mode

Frame length < dotRTSThreashold



for 'long' frames, you want to reduce the probability of collision with some overhead



### Two problem in WLAN

#### Hidden terminal problem

C is transmitting to B but A didn't know B exist

A is also sending packet to C thus, collision occur

Solution exist CSMA/CA collision avoidance 

#### Exposed terminal problem

A sending message to D

B knows that someone is transmitting

B can transmit to C without any collision

but B didn't transmit since B doesn't where D is

The problem is due to B exposed to A'TX no solution right now



### CSMA/Collision Avoid

Physical level sensing collision: implemented in the receiver hardware

Virtual carrier sensing: using a counter(Called NAV at each node)

if counter > 0 most likely someone is transmitting

if counter = 0 no one is transmitting

condition for transmitting mediums is idle i.e. NAV = 0 and carrier is absent



why no Collision detection in WLAN

```
Wireless transceivers can't send and receive on the same channel at the same time, so they can't detect collisions. This is due to the fact that there's an incredible difference between send power (generally around 100mw) and receive sensitivity (commonly around 0.01 to 0.0001mw). The sending would cover up any possible chance of receiving a foreign signal, no chance of "Collision Detection". For this reason Collision Avoidance with Control Messages is necessary.
```



## Principles of reliable data transfer

no dup, no loss, no error, no reordering



### Rdt 1.0: reliable transfer over a reliable channel

- underlying channel prefect reliable
  - no bit error
  - no loss of packets
- separe FSMs for sender, receiver:
  - sender sends data into underlying channel
  - receiver reads data from underling channel

### Rdt 2.0: channel with bits error

- error detection, cannot fix at receiver because it is expensive
- receiver send packet has error back: 1. re-send packet at NAK or send packet at Next ACK
- fatal flaw if ACK or NAK has error, need to resend and handling duplicate (use sequence number)

### Rdt 3.0: channel with packet loss

- resend packet if no ACK received after certain time
- if delay channel can handle packet duplicate

