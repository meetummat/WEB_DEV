# Computer Networks — Complete Notes

Complete study notes for Computer Networks covering Web Development, Software Development, and Technical Interviews.

---

## Part 1 — Computer Network Fundamentals

### 1. Computer Network

**Definition:** A computer network is a group of two or more computing devices connected together so they can exchange data and share resources.

**Why it is needed:** A single isolated computer cannot share files, printers, or internet access with another computer. Networking solves this by giving devices a common way to talk to each other.

**How it works:** Devices are connected through wired or wireless media, and they follow shared rules called **protocols** so that data sent by one device can be correctly understood by another.

**Example:** Your laptop, phone, and smart TV connected to the same home Wi-Fi router form a small computer network.

**Related concepts:** Network Components (2), Internet (5), LAN (27).

### 2. Network Components

**Definition:** The basic building blocks required for a network to function.

**What it means:** Every network — no matter how small or large — is made of the same core ingredients:

- **End devices (hosts):** computers, phones, servers, IoT devices.
- **Intermediate devices:** hubs, switches, routers, access points (see Part 4).
- **Transmission media:** cables or wireless signals that carry the data (24).
- **Protocols:** agreed-upon rules for communication (e.g. TCP/IP).
- **Network software/services:** operating system networking stack, DNS, DHCP, etc.

**Important points:** A network is not just cables — it needs devices, media, and protocols working together.

### 3. Client-Server Architecture

**Definition:** A network model where dedicated **server** machines provide services (files, web pages, email) and **client** machines request and consume those services.

**How it works:** The client sends a request over the network; the server listens for requests, processes them, and sends back a response.

**Example:** Your browser (client) requests `https://google.com`; Google's servers respond with the web page.

**Important points:**

- Centralized — easier to secure, back up, and manage.
- Server can become a bottleneck or single point of failure if not scaled properly.

**Related concepts:** Peer-to-Peer Architecture (4), HTTP (142).

### 4. Peer-to-Peer (P2P) Architecture

**Definition:** A network model where every device (peer) can act as both a client and a server — there is no dedicated central server.

**How it works:** Peers directly share resources (files, processing power) with each other.

**Example:** BitTorrent file sharing, where each downloader also uploads pieces of the file to other peers.

**Comparison — Client-Server vs P2P:**

| Aspect | Client-Server | Peer-to-Peer |
|---|---|---|
| Control | Centralized | Decentralized |
| Scalability | Limited by server capacity | Can spread load across peers, though this depends on peer availability and network conditions rather than scaling automatically |
| Setup cost | Higher (dedicated servers) | Lower |
| Reliability | Server failure = outage | Can reduce dependence on a single central server |

### 5. Internet

**Definition:** The Internet is a global "network of networks" — The Internet is a global network of interconnected networks that communicate using the Internet Protocol suite.

**What it means:** No single organization owns the Internet. It is a cooperative interconnection of ISPs, data centers, and organizational networks, all agreeing to use the same addressing (IP) and routing rules.

**How it works:** Data is broken into packets (14), each carrying source/destination IP addresses. Routers (41) forward these packets across networks until they reach the destination, largely using undersea fibre-optic cables and terrestrial links between continents.

**Important points:**

- The Internet is physical (cables, routers, data centers) *and* logical (protocols, addressing).
- Data physically travels through wires/fibre (and some wireless/satellite links) at close to the speed of light in the medium.

**Related concepts:** ARPANET (6), IP Address (46), Routing (104).

### 6. ARPANET

**Definition:** ARPANET (Advanced Research Projects Agency Network) was one of the earliest major operational packet-switching networks and an important predecessor of today's internet, developed by the U.S. Department of Defense in the late 1960s, and is considered the ancestor of today's Internet.

**Why it matters:** It proved that packet switching (22) — breaking data into small packets routed independently — was a workable alternative to old circuit-switched telephone networks, laying the foundation for the modern Internet.

**Important points:** ARPANET connected its first nodes in 1969; TCP/IP was later adopted as its standard protocol in the 1980s, which is essentially the birth of the modern Internet.

### 7. Analog Signal

**Definition:** A continuous signal that varies smoothly over time, capable of taking any value within a range.

**Example:** The human voice, or a traditional telephone line signal, is analog — the voltage changes continuously with the sound wave.

**Related concepts:** Digital Signal (8), Modem (9).

### 8. Digital Signal

**Definition:** A signal that represents data using discrete values — typically just two levels (0 and 1, i.e., binary).

**What it means:** Computers internally represent everything (text, images, video) as binary digits. A digital signal is the electrical/optical representation of that binary data — on/off, high-voltage/low-voltage.

**Comparison — Analog vs Digital:**

| Aspect | Analog | Digital |
|---|---|---|
| Values | Continuous range | Discrete (0/1) |
| Noise resistance | Poor (degrades with noise) | Good (easy to regenerate) |
| Example medium | Old telephone lines | Modern Ethernet, fibre, Wi-Fi |

### 9. Modem

**Definition:** MODEM stands for **Mo**dulator-**Dem**odulator — a device that converts digital data from a computer into analog signals for transmission over analog lines (modulation), and converts incoming analog signals back into digital data (demodulation).

**Why it is needed:** Older telephone lines were analog, but computers work in digital data. A modem bridges this gap so digital devices can communicate over analog infrastructure.

**Important points:** Modern access devices such as cable modems and fiber ONTs perform the appropriate signal/interface conversion between the ISP access network and the customer's local network.

### 10. Data Communication

**Definition:** The exchange of data between two devices via some form of transmission medium.

**Key characteristics of effective data communication:**

- **Delivery** — data must reach the correct destination.
- **Accuracy** — data must be delivered without alteration.
- **Timeliness** — data must arrive in a useful time frame (real-time for video/audio).
- **Jitter** — variation in packet arrival time should be minimal, especially for streaming.

### 11. Bandwidth

**Definition:** The maximum rate at which data can be transferred over a network connection, usually measured in bits per second (bps, Kbps, Mbps, Gbps).

**What it means:** Think of bandwidth as the "width of the pipe" — a higher bandwidth connection can carry more data per second, not necessarily faster per bit.

**Example:** A 100 Mbps connection can theoretically transfer 100 megabits of data every second.

**Related concepts:** Throughput (13), Latency (12).

### 12. Latency

**Definition:** The time delay between sending a request and receiving the first response — essentially how long it takes data to travel from source to destination.

**Example:** Ping time to a server (e.g., 20 ms) is a common real-world measurement of latency.

**Important points:** Low latency matters most for real-time applications (gaming, video calls); high bandwidth alone does not guarantee low latency.

### 13. Throughput

**Definition:** The actual amount of data successfully transferred over a network in a given time — the real-world performance, as opposed to bandwidth's theoretical maximum.

**Comparison — Bandwidth vs Throughput:** Bandwidth is the capacity of the pipe; throughput is how much water is actually flowing through it right now (affected by congestion, errors, overhead).

### 14. Packet

**Definition:** A formatted unit of data, containing both the actual payload and control information (headers), used to carry data across a packet-switched network — primarily the term used at the Network layer.

**Why it is needed:** Breaking data into packets lets multiple devices share the same medium efficiently, allows different packets to take different routes, and makes error recovery easier (only the lost packet needs retransmission, not the whole message).

**Related concepts:** Segment (15), Datagram (16), Frame (17), Encapsulation (18).

### 15. Segment

**Definition:** The unit of data at the **Transport layer** (TCP). A segment includes the actual data plus TCP header fields like source/destination port, sequence number, and acknowledgment number.

### 16. Datagram

**Definition:** The unit of data at the **Network layer** when using a connectionless protocol — most commonly used to describe an IP packet (also called an IP datagram) or a UDP message at the transport layer.

**Important points:** "Packet" is often used as a general term, while "datagram" specifically emphasizes that each unit is routed independently, with no guaranteed delivery or order (connectionless).

### 17. Frame

**Definition:** The unit of data at the **Data Link layer**, consisting of the Network-layer packet plus a Data Link header (containing MAC addresses) and trailer (containing error-checking information like a CRC).

**Related concepts:** Framing (93), MAC Address (71).

### 18. Encapsulation

**Definition:** The process of wrapping data with protocol-specific headers (and sometimes trailers) as it moves down the OSI/TCP-IP layers, from Application down to Physical.

**How it works, step by step:**

```
Application data
   -> [TCP Header | Data]                    (Segment - Transport layer)
   -> [IP Header | TCP Header | Data]         (Packet  - Network layer)
   -> [Frame Header | IP Header | TCP Header | Data | Frame Trailer]  (Frame - Data Link layer)
   -> bits transmitted as electrical/optical/radio signals (Physical layer)
```

Each layer adds its own header (like nesting an envelope inside another envelope) before passing the data down to the layer below.

**Related concepts:** Decapsulation (19), OSI Model (85), TCP/IP Model (131).

### 19. Decapsulation

**Definition:** The reverse of encapsulation — as data moves up the layers at the receiving device, each layer strips off and reads its corresponding header, until only the original application data remains.

**Example:** A router only needs to decapsulate up to the Network layer (to read the IP header and decide where to forward the packet), while the final destination host decapsulates all the way up to the Application layer.

## Part 2 — Data Transmission & Switching

### 20. Circuit Switching

**Definition:** A switching method where a dedicated communication path (circuit) is established between sender and receiver for the entire duration of the session, before any data is sent.

**How it works:** Think of an old telephone call — a physical/logical path is reserved end-to-end, and it stays reserved (even during silence) until the call ends.

**Important points:**

- Guarantees a consistent, dedicated bandwidth once set up.
- Wastes capacity during idle periods, because the circuit is reserved regardless of use.
- Example: traditional landline telephone networks.

### 21. Message Switching

**Definition:** A switching method where the entire message is sent as one block from node to node ("store-and-forward"), with each intermediate node storing the complete message before forwarding it to the next node.

**Important points:**

- No dedicated path is reserved in advance.
- Can cause high storage requirements and delay at intermediate nodes, since the whole message must arrive before forwarding.
- Largely historical (used in old telegraph/email-relay systems); not used in modern networks.

### 22. Packet Switching

**Definition:** A switching method where data is broken into small, independently routed units called packets. Each packet may take a different path to the destination and is reassembled there.

**How it works:** Each packet carries a header with source/destination addresses. Routers examine this header and forward each packet independently, often via the best currently-available path.

**Why it is needed:** Allows efficient sharing of network links among many users simultaneously, and improves fault tolerance — if one path fails, packets can be rerouted.

**Important points:** This is the switching method used by the modern Internet.

### 23. Comparison of Switching Techniques

| Aspect | Circuit Switching | Message Switching | Packet Switching |
|---|---|---|---|
| Path | Dedicated, reserved | No dedicated path | No dedicated path |
| Data unit | Continuous stream | Whole message | Small packets |
| Resource use | Wasteful when idle | Efficient, but slow | Efficient |
| Delay | Low once connected, but setup delay | High (store whole message) | Low, variable |
| Used today | Legacy telephony | Rare/historical | Modern Internet |

### 24. Transmission Media

**Definition:** The physical or wireless path through which data signals travel from sender to receiver.

**What it means:** Transmission media is broadly split into **guided (wired)** media, where signals travel along a physical conductor, and **unguided (wireless)** media, where signals travel through free space.

**Related concepts:** Wired Communication (25), Wireless Communication (26).

### 25. Wired Communication

**Definition:** Data transmission through a physical conducting medium.

**Common types:**

- **Twisted Pair Cable** (e.g., Ethernet Cat5e/Cat6) — copper wires twisted together to reduce electromagnetic interference; used in most LANs.
- **Coaxial Cable** — a central copper conductor surrounded by insulation and shielding; used in cable internet/TV.
- **Fibre-Optic Cable** — transmits data as pulses of light through glass/plastic fibre; very high bandwidth, low signal loss, used for backbone/undersea links.

**Important points:** Undersea fibre-optic cables physically connect continents and carry the vast majority of international internet traffic.

### 26. Wireless Communication

**Definition:** Data transmission through free space using electromagnetic waves (radio, microwave, infrared).

**Common types:** Wi-Fi (radio waves, short-to-medium range), Bluetooth (short range), Cellular/Mobile data (4G/5G, wide range via cell towers), Satellite links (very long range, higher latency).

**Comparison — Wired vs Wireless:**

| Aspect | Wired | Wireless |
|---|---|---|
| Speed/reliability | Generally higher, more stable | Can vary with interference/distance |
| Mobility | None (fixed) | High |
| Security | Harder to intercept | Easier to intercept (needs encryption) |
| Installation | More effort (cabling) | Easier/faster to deploy |

## Part 3 — Types of Networks

### 27. LAN (Local Area Network)

**Definition:** A network that connects devices within a small, limited geographic area, such as a home, office, or single building.

**Characteristics:** High speed, low latency; usually owned and managed by a single organization/individual; devices are often on the same private IP range.

**Example:** A home Wi-Fi network, or an office network connecting all employee desktops.

### 28. MAN (Metropolitan Area Network)

**Definition:** A network spanning a larger area than a LAN but smaller than a WAN — typically covering a city.

**Example:** City-wide public Wi-Fi, or a cable-TV network serving an entire metropolitan area, formed by interconnecting multiple LANs.

### 29. WAN (Wide Area Network)

**Definition:** A network that spans a broad geographic area — across cities, countries, or continents — usually connecting multiple LANs/MANs together.

**Example:** The Internet itself is the largest WAN; a company's private network connecting offices in different countries is also a WAN.

**Comparison — LAN vs MAN vs WAN:**

| Aspect | LAN | MAN | WAN |
|---|---|---|---|
| Coverage | Building/campus | City | Country/global |
| Speed | Highest | Medium | Lowest (relatively) |
| Ownership | Single org | One or few orgs | Multiple orgs/ISPs |
| Example | Home Wi-Fi | City cable network | The Internet |

### 30. PAN (Personal Area Network)

**Definition:** A very short-range network built around a single person's immediate devices, typically within a few meters.

**Example:** Bluetooth connection between your phone and wireless earbuds, or a smartwatch synced to your phone.

### 31. Network Topologies

**Definition:** The arrangement/layout pattern in which devices and connections in a network are physically or logically organized.

**Why it matters:** Topology affects cost, fault tolerance, ease of troubleshooting, and scalability of a network.

**Types covered below:** Bus (32), Star (33), Ring (34), Mesh (35), Hybrid (36).

### 32. Bus Topology

**Definition:** All devices are connected to a single shared central cable (the "bus" or backbone), and data travels along this cable in both directions.

**Working:** A device sends data onto the shared cable; every other device "sees" the data, but only the intended recipient (matched by address) accepts it — the rest discard it.

```
Device1 --- Device2 --- Device3 --- Device4
       (single shared backbone cable)
```

**Advantages:** Easy and cheap to set up; requires less cable than other topologies.

**Disadvantages:** If the main cable fails, the entire network goes down; performance degrades as more devices are added (more collisions on the shared medium).

**Use case:** Small, simple, low-cost legacy networks. Rarely used today.

### 33. Star Topology

**Definition:** All devices are connected individually to a central device (hub or switch); no device connects directly to another.

**Working:** Every message from one device to another passes through the central hub/switch first.

```
        [Switch/Hub]
        /    |    \
   Device1 Device2 Device3
```

**Advantages:** If one connection/cable fails, only that device is affected — rest of network keeps working; easy to add/remove devices; easy to troubleshoot.

**Disadvantages:** If the central hub/switch fails, the entire network goes down; needs more cabling than bus topology.

**Use case:** The most common topology in modern LANs (homes and offices), because switches make it reliable and manageable.

### 34. Ring Topology

**Definition:** Each device is connected to exactly two neighboring devices, forming a closed loop (ring). Data travels around the ring, hop by hop, until it reaches its destination.

**Working:** Data may travel in one direction (unidirectional ring) or both directions (dual ring, for redundancy).

```
Device1 -- Device2
   |          |
Device4 -- Device3
```

**Advantages:** Data travels at predictable, high speed with no collisions (with token-passing); faults are relatively easy to isolate.

**Disadvantages:** A single failed device/link can disrupt the whole ring (unless it's a dual ring); adding/removing a device is disruptive.

**Use case:** Historically used in Token Ring and FDDI networks; rare in modern practice.

### 35. Mesh Topology

**Definition:** Every device is connected to every other device (full mesh) or to several other devices (partial mesh), providing multiple possible paths for data.

**Working:** If one path/link fails, data can be rerouted through an alternate path.

```
Device1 --- Device2
   |  \      /  |
   |   \    /   |
Device4 --- Device3
(each device connects to every other)
```

**Advantages:** Highly reliable and redundant; failure of one link doesn't isolate any device.

**Disadvantages:** Very expensive and complex — cabling grows quadratically with the number of devices (n(n-1)/2 links for full mesh); difficult to manage at scale.

**Use case:** Critical backbone links (ISP core networks, military/government networks) where reliability matters more than cost.

### 36. Hybrid Topology

**Definition:** A combination of two or more different topologies, tailored to fit an organization's specific needs (e.g., star-bus, star-ring).

**Advantages:** Flexible, scalable, can be designed around real-world constraints and requirements.

**Disadvantages:** More complex to design/implement, and can be costlier depending on which topologies are combined.

**Use case:** Large enterprise networks — e.g., star topology within each department, connected together via a backbone bus or ring.

**Comparison summary — all topologies:**

| Topology | Fault tolerance | Cost | Ease of adding devices | Common use today |
|---|---|---|---|---|
| Bus | Low | Low | Moderate | Rare/legacy |
| Star | Medium (hub is SPOF) | Medium | Easy | Very common (LANs) |
| Ring | Low (single ring) | Medium | Hard | Rare/legacy |
| Mesh | Very high | Very high | Hard | Critical backbones |
| Hybrid | Depends on mix | Depends | Depends | Large enterprises |

## Part 4 — Network Devices

### 37. Hub

**Definition:** A basic Physical-layer (Layer 1) device that connects multiple devices in a network and simply repeats/broadcasts incoming data out to **all** connected ports, regardless of the intended recipient.

**Important points:** Does not read addresses or make forwarding decisions; causes more collisions and wastes bandwidth; largely obsolete, replaced by switches.

### 38. Switch

**Definition:** A Data Link-layer (Layer 2) device that connects multiple devices in a LAN and intelligently forwards data only to the specific port where the destination device (identified by MAC address) is connected.

**How it works:** A switch builds and maintains a MAC Address Table (77) by learning which MAC address is reachable on which port, then forwards frames only to the relevant port instead of broadcasting to all.

**Important points:** Far more efficient than a hub; eliminates unnecessary collisions; the backbone device of modern star-topology LANs.

**Related concepts:** MAC Address Table (77), Star Topology (33).

### 39. Bridge

**Definition:** A Data Link-layer device that connects two network segments (often two smaller LANs) and filters traffic between them based on MAC addresses, reducing unnecessary traffic crossing between segments.

**Important points:** A switch is essentially a multi-port bridge; bridges are largely a historical stepping stone to modern switches.

### 40. Repeater

**Definition:** A Physical-layer device that receives a signal and regenerates/retransmits it — used to extend the distance a signal can travel without degrading.

**Why it is needed:** Signals weaken (attenuate) over distance; a repeater restores signal strength so it can travel further.

**Example:** A Wi-Fi range extender is a common modern repeater.

### 41. Router

**Definition:** A Layer 3 device that forwards packets between networks using IP addresses and a routing table to decide the preferred/best path according to its routing information. Many home and office routers also perform NAT (69), though NAT is a common additional function rather than a defining requirement of what makes a device a router.

**How it works:** A router examines the destination IP address of each incoming packet, consults its routing table, and forwards the packet out the appropriate interface toward its destination network.

**Important points:**

- A router connects different networks (e.g., your home LAN to your ISP's network), unlike a switch, which connects devices *within* one network.
- Also typically performs NAT (69) for home/office networks, translating private IPs to a public IP.
- A router maintains interface IP addresses/prefixes and routing information used to determine where packets should be forwarded.
- Unlike end devices (which implement all 7 OSI layers), a traditional router primarily operates through the Network layer (Physical, Data Link, Network) for its core job of forwarding packets.

**Related concepts:** Routing (104), NAT (69), Default Gateway (107).

### 42. Gateway

**Definition:** A gateway connects a network to another network. In some contexts it can also translate between protocols. A default gateway is the router used to reach other networks (see 107).

**Important points:** In home networking, "default gateway" simply refers to the router that connects your LAN to the wider Internet. Some gateways translate between fundamentally different protocol stacks (e.g., connecting a legacy system to a modern IP network), but that translation role is one possible function of a gateway rather than a universal requirement.

### 43. Network Interface Card (NIC)

**Definition:** The hardware component (physical or virtual) inside a device that allows it to connect to a network. A NIC is associated with a MAC address. Physical interfaces may have a factory-assigned address, while virtual interfaces and modern operating systems can use software-assigned or locally administered addresses.

**Important points:**

- A device can have multiple NICs (e.g., a laptop with both Wi-Fi and Ethernet), and therefore multiple MAC addresses — one per NIC.
- Command to check NICs/MAC addresses: `networksetup -listallhardwareports` (macOS) or `getmac /v /fo list` (Windows).

**Related concepts:** MAC Address (71), OUI (73).

### 44. Modem

See **Modem (9)** in Part 1 — a modem is the device that converts between digital data and the analog/physical-layer signal used by the ISP's access network (e.g., DSL, cable, fibre).

### 45. Access Point (AP)

**Definition:** A device that allows wireless (Wi-Fi) devices to connect to a wired network, effectively acting as a bridge between the wireless and wired parts of a LAN.

**Important points:** A typical home "Wi-Fi router" is really a combo device — router + switch + access point + (sometimes) modem, all built into one box.

**Device/Layer summary:**

| Device | Primary OSI Layer | Role |
|---|---|---|
| Repeater | Physical (1) | Regenerate signal |
| Hub | Physical (1) | Broadcast to all ports |
| Bridge | Data Link (2) | Filter between 2 segments |
| Switch | Data Link (2) | Forward by MAC address |
| Access Point | Data Link (2) | Wireless-to-wired bridge |
| Router | Network (3) | Forward by IP address, connect networks |
| Gateway | Varies (often above Network) | Translate between protocol stacks |

## Part 5 — IP Addressing

### 46. IP Address

**Definition:** An IP (Internet Protocol) address is a numerical address assigned to a network interface, used to identify its location on a network and enable routing of data to it.

**What it means:** Just like a postal address identifies a house so mail can be delivered, an IP address identifies a network interface so packets can be routed to it across a network. (In everyday conversation this is often shortened to "the device's IP address," since most simple devices have just one active network interface — but strictly, the address belongs to the interface, which is why a device with multiple interfaces, such as both Wi-Fi and Ethernet, can have a different IP address on each.)

**Why it is needed:** Without a unique address, routers would have no way to know where to deliver a packet.

**How it works:** Every device connected to a network is assigned an IP address, either by an ISP, a router's DHCP service, or manually. Routers use the destination IP address in each packet's header to decide where to forward it.

**Related concepts:** IPv4 (47), IPv6 (48), Subnet Mask (66), MAC Address (71) — see (75) for the IP vs MAC distinction.

### 47. IPv4

**Definition:** Internet Protocol version 4 — a 32-bit address, usually written as four decimal numbers (0–255) separated by dots, called "dotted-decimal notation."

**Example:** `192.168.1.10`

**Important points:** 32 bits gives about 4.3 billion possible addresses — insufficient for today's number of internet-connected devices, which is the main reason IPv6 was created and why NAT (69) is so widely used.

### 48. IPv6

**Definition:** Internet Protocol version 6 — a 128-bit address, written as eight groups of four hexadecimal digits separated by colons.

**Example:** `2001:0db8:85a3:0000:0000:8a2e:0370:7334`

**Why it is needed:** IPv4's ~4.3 billion addresses are effectively exhausted; IPv6 provides an astronomically larger address space (2^128 addresses), enough for every device to have its own public address without relying on NAT.

**Important points:** IPv4 and IPv6 are gradually running in parallel ("dual stack") during the long transition period; not all networks support IPv6 yet.

### 49. Public IP Address

**Definition:** An IP address that is globally unique and routable directly on the Internet.

**Important points:** Assigned by an ISP; this is the address the outside world sees when your device communicates with the Internet (often the router's WAN-facing address; with CGNAT, the ISP may perform another layer of NAT, thanks to NAT).

### 50. Private IP Address

**Definition:** An IP address reserved for use within private/local networks only — not routable on the public Internet.

**Private IPv4 ranges (reserved by IANA for private use):**

| Class | Range | Approx. address count |
|---|---|---|
| Class A private | 10.0.0.0 – 10.255.255.255 | ~16.7 million |
| Class B private | 172.16.0.0 – 172.31.255.255 | ~1 million |
| Class C private | 192.168.0.0 – 192.168.255.255 | ~65,000 |

**Why it is needed:** Lets every home/office network reuse the same private address ranges internally, without conflicting with the public Internet's address space — this is what makes NAT (69) possible and hugely reduces the demand for scarce public IPv4 addresses.

**Related concepts:** NAT (69), LAN (27).

### 51. Static IP Address

**Definition:** An IP address that is manually configured and does not change over time.

**Use case:** Servers, printers, and devices that need a consistent, predictable address (e.g., a web server so DNS records always point to the correct address).

### 52. Dynamic IP Address

**Definition:** An IP address automatically assigned to a device by a DHCP server, and which can change over time (e.g., on reconnect or lease expiry).

**Use case:** Most home/office client devices (laptops, phones) use dynamic IPs for convenience — no manual configuration needed.

**Related concepts:** DHCP (141).

### 53. IPv4 Address Classes

**Definition:** The original (1981) system of dividing the IPv4 address space into five classes (A–E), based on the value of the first few bits/first octet, mainly to define default network/host boundaries.

**Important note:** Classful addressing is now largely a **historical/legacy concept**. Since the 1990s, the Internet has used **CIDR (67)** with subnet masks instead — networks are no longer restricted to fixed class boundaries. Classes are still worth knowing (they explain private-range naming and are foundational for exams/interviews), but modern real-world addressing is classless.

### 54. Class A

**Range:** `1.0.0.0` to `126.255.255.255` (first bit is always `0`)
**Default mask:** `/8` — Networks: 128 (fewer usable, since some are reserved); Hosts per network: over 16 million.
**Purpose:** Very large networks/organizations.

### 55. Class B

**Range:** `128.0.0.0` to `191.255.255.255`
**Default mask:** `/16` — Networks: 16,384; Hosts per network: about 65,000.
**Purpose:** Medium-sized networks.

### 56. Class C

**Range:** `192.0.0.0` to `223.255.255.255`
**Default mask:** `/24` — Networks: over 2 million; Hosts per network: about 254.
**Purpose:** Small networks (most home/office private networks, e.g., `192.168.x.x`, effectively behave like this range).

### 57. Class D

**Range:** `224.0.0.0` to `239.255.255.255`
**Purpose:** Class D: 224–239. Used for multicast communication — sending data to a group of interested recipients simultaneously (see Multicast, 84), rather than one recipient (Unicast, 82) or all devices (Broadcast, 83). Provides roughly 2^28 addresses for multicast group use.

### 58. Class E

**Range:** `240.0.0.0` to `255.255.255.255`
**Purpose:** Reserved by IANA for experimental/future use; not assigned for standard networking (~2^28 addresses reserved).

### 59. Network ID

**Definition:** The portion of an IP address that identifies which network a device belongs to (shared by every device on that network).

**How it's determined:** Found by applying the subnet mask (66) to the IP address — bits where the mask is `1` belong to the network portion.

### 60. Host ID

**Definition:** The portion of an IP address that identifies a specific device within its network — unique per device on that network, while the network ID stays the same for everyone on it.

**Example:** In `192.168.1.25/24`, the network ID is `192.168.1.0` and the host ID is `.25`.

### 61. Network Address

**Definition:** The special address within a subnet where **all host bits are 0** — it identifies the network itself and is not assignable to any individual device.

**Example:** For `192.168.1.0/24`, the network address is `192.168.1.0`.

### 62. Broadcast Address

**Definition:** The special address within a subnet where **all host bits are 1** — used to send data to *every* device on that subnet at once.

**Example:** For `192.168.1.0/24`, the broadcast address is `192.168.1.255`.

**Important points:** Because the network address and broadcast address are both reserved, a `/24` subnet with 256 total addresses only has 254 **usable** host addresses.

### 63. Loopback Address

**Definition:** A reserved IP address (`127.0.0.0/8`, most commonly `127.0.0.1`) that a device uses to refer to itself — traffic sent here never leaves the device; it "loops back" internally.

**Use case:** Testing whether a device's own network stack is working (e.g., `ping 127.0.0.1`), or running local development servers (`localhost`).

### 64. IANA (Internet Assigned Numbers Authority)

**Definition:** IANA coordinates global IP address allocation, DNS root-zone management, and protocol parameters (such as port number assignments).

**How it works:** IANA allocates large blocks of IP addresses to **Regional Internet Registries (RIRs)** on a continent-wise basis (e.g., ARIN for North America, RIPE NCC for Europe, APNIC for Asia-Pacific), which then allocate smaller blocks to ISPs, who in turn assign addresses to end users.

**Important points:** Fixed bit patterns and address ranges within each class are defined and reserved by IANA; Class D and E ranges are also reserved by IANA (see 57, 58).

### 65. ISP and IP Allocation

**Definition:** An Internet Service Provider (ISP) is a company that provides Internet access to individuals/organizations, and is responsible for allocating IP addresses (public, and often the private range setup) to its customers.

**How it works:** ISPs receive or obtain IP address prefixes/blocks through the Internet number-allocation system and assign smaller prefixes or addresses to customers, then assign individual public IP addresses (static or dynamic) to customers out of that block.

**Analogy:** Similar in structure to how mobile phone numbers are distributed — telecom regulators allocate number-range blocks to carriers, who then assign individual numbers to subscribers; IANA→RIR→ISP works the same way for IP addresses.

### 66. Subnet Mask

**Definition:** A 32-bit value used alongside an IP address to divide it into its network portion and host portion.

**What it means:** The subnet mask has `1`s over the network-ID bits and `0`s over the host-ID bits. Applying it (bitwise AND) to an IP address reveals the network address.

**How it works — example:**

```
IP address:    192.168.1.25
Subnet mask:   255.255.255.0   (i.e., /24 — first 24 bits are network bits)

Binary AND:
192.168.1.25   = 11000000.10101000.00000001.00011001
255.255.255.0  = 11111111.11111111.11111111.00000000
-----------------------------------------------------
Network ID     = 11000000.10101000.00000001.00000000 = 192.168.1.0
```

So this device belongs to network `192.168.1.0`, and its host portion is `25`.

**Important points:**

- The subnet mask is stored in routers/devices and used every time a routing/forwarding decision is made.
- `/8`, `/16`, `/24` etc. (CIDR notation) is a shorthand for how many leading bits are `1` in the mask.

**Related concepts:** Network ID (59), CIDR (67), Subnetting (68).

### 67. CIDR (Classless Inter-Domain Routing)

**Definition:** A modern IP addressing scheme (introduced 1993) that replaced rigid classful addressing (53) with flexible, arbitrary-length network prefixes, written as `IP/prefix-length` (e.g., `10.20.0.0/20`).

**Why it is needed:** Classful addressing wasted huge numbers of addresses (e.g., a company needing 300 addresses had to be given an entire Class B block of 65,000). CIDR allows allocating exactly the number of addresses needed, and lets ISPs aggregate ("summarize") many small networks into a single routing table entry — reducing the size of global routing tables.

**Example:** `8.0.0.0/8` means the first 8 bits are the fixed network portion — the same idea as classful Class A, but CIDR allows *any* prefix length, e.g., `/20`, `/27`, not just `/8`, `/16`, `/24`.

### 68. Subnetting

**Definition:** The process of dividing one larger network into multiple smaller sub-networks (subnets), by "borrowing" bits from the host portion to extend the network portion.

**Why it is needed:** Improves address utilization, reduces broadcast traffic (smaller broadcast domains), and allows logical separation of departments/regions within one organization.

**How to find the Network ID via subnetting — worked example:**

Suppose you're given the block `192.168.1.0/24` and need to split it into 4 smaller subnets.

- Original: `192.168.1.0/24` → 256 addresses, 254 usable hosts.
- To make 4 subnets, borrow 2 more host bits (2² = 4) → new prefix `/26`.
- Each subnet now has 2^(32-26) = 64 addresses (62 usable hosts).

```
Subnet 1: 192.168.1.0   /26   (hosts: .1  – .62,  broadcast .63)
Subnet 2: 192.168.1.64  /26   (hosts: .65 – .126, broadcast .127)
Subnet 3: 192.168.1.128 /26   (hosts: .129– .190, broadcast .191)
Subnet 4: 192.168.1.192 /26   (hosts: .193– .254, broadcast .255)
```

Each subnet's **first address** is its Network ID, and its **last address** is its Broadcast Address (62).

**Important points:** The first (network) and last (broadcast) address of *every* subnet are reserved and not assignable to a host.

### 69. NAT (Network Address Translation)

**Definition:** A technique, commonly performed by routers, that translates IP addresses between address realms — most commonly between the private addresses used inside a LAN and a public address used on the Internet — and does the reverse translation for return traffic.

**Why it is needed:** IPv4 public addresses are scarce; NAT commonly lets an entire home/office of devices with private IPs share one or more public IPs to access the Internet.

**How it works — example (the common private-to-public case):**

```
Laptop (192.168.1.10) --\
Phone  (192.168.1.11) ---> [Router doing NAT] --- Public IP: 203.0.113.5 ---> Internet
Smart TV (192.168.1.12)-/
```

The router keeps a translation table mapping each internal (private IP, port) pair to a unique (public IP, port) pair, so return traffic from the Internet can be correctly routed back to the right internal device.

**Important points:** Your device's own private IP never actually changes when browsing the Internet — only the router's NAT translation makes it *appear* to the outside world as the router's single public IP.

**Related concepts:** PAT (70), Private IP Address (50), Public IP Address (49).

### 70. PAT (Port Address Translation)

**Definition:** A more specific/common form of NAT (sometimes called "NAT overload") where multiple private IP addresses are mapped to a **single** public IP address, distinguished from each other by unique port numbers.

**How it works:** Each outgoing connection from an internal device gets assigned a unique source port on the router's public IP, so the router can tell which internal device a piece of return traffic belongs to.

**Example:** `192.168.1.10:5000` and `192.168.1.11:5000` both go out as `203.0.113.5:61001` and `203.0.113.5:61002` respectively — different external ports let the router distinguish and route return traffic to the correct internal device.

**Important points:** PAT is what most home routers actually use (commonly just called "NAT" in everyday conversation) — it's how one public IP can serve many simultaneous devices/connections.

## Part 6 — MAC Address & Local Network Communication

### 71. MAC Address

**Definition:** Media Access Control Address — a 48-bit Layer 2 (link-layer) address associated with a network interface, used to identify it within a local network segment (LAN).

**What it means:** While an IP address can change depending on which network you connect to, a MAC address is associated with a specific network interface (NIC) rather than with the network it's currently joined to.

**Important points:** A NIC is typically assigned a MAC address. Physical interfaces often have a factory-assigned address, while virtual interfaces and modern operating systems can use software-assigned or locally administered addresses instead. Most operating systems also allow the in-use MAC address to be overridden in software ("MAC spoofing" or "MAC randomization") — so it is not accurate to say a MAC address can never change. Address randomization is commonly and legitimately used for privacy (e.g., many modern phones randomize their MAC address while Wi-Fi scanning), but overriding a MAC address to impersonate another device or evade a network ban can be against network policy or illegal depending on context.

**Related concepts:** NIC (43), OUI (73), MAC vs IP (75).

### 72. MAC Address Structure

**Definition:** A MAC address is 48 bits long, written as 12 hexadecimal digits, grouped in pairs separated by colons or hyphens.

**Example:** `7a:cb:f1:3f:db:23`

**Structure:**

```
7a:cb:f1 : 3f:db:23
--------   --------
  OUI      Device/interface-specific identifier
(first 24 bits, vendor)  (last 24 bits, interface identifier)
```

### 73. OUI (Organizationally Unique Identifier)

**Definition:** The first 24 bits (first 3 bytes/6 hex digits) of a MAC address, assigned to a specific hardware manufacturer by the IEEE.

**Why it is needed:** For globally administered MAC addresses, the OUI identifies the organization associated with the assigned prefix. Locally administered/randomized addresses may not provide reliable manufacturer identification.

### 74. NIC and MAC Addresses

**Definition:** A device can have as many MAC addresses as it has Network Interface Cards — one MAC address per NIC (physical or virtual).

**Example:** A laptop with both Wi-Fi and Ethernet has two NICs and therefore two distinct MAC addresses — one per interface. A device can effectively have as many MAC addresses as it has ways of connecting to a network.

**Command to check:** `networksetup -listallhardwareports` (macOS), `getmac /v /fo list` (Windows).

### 75. MAC Address vs IP Address

| Aspect | MAC Address | IP Address |
|---|---|---|
| Layer | Data Link (Layer 2) — link-layer address associated with a network interface | Network (Layer 3) — logical address; may be private/local or globally routable depending on the address |
| Assigned by | Often factory-assigned (physical interfaces); can be software-assigned or overridden | ISP / DHCP / network admin |
| Scope | Used within a local network segment; not typically forwarded beyond it | Used for routing across networks; may be private (local only) or public (Internet-routable) |
| Changes when | Rarely (unless spoofed/reassigned) | Often (per network/DHCP lease) |
| Format | 48-bit hex (e.g., `7a:cb:f1:3f:db:23`) | 32-bit (IPv4) or 128-bit (IPv6) |
| Used for | Delivery within a local network segment | Delivery across networks (routing) |

**Important points:** Within a single LAN, devices can actually communicate using just MAC addresses (no IP address lookup needed for the local hop) — but routing data *across* networks always requires IP addresses.

### 76. Ethernet

**Definition:** The dominant family of wired LAN technologies and framing standards, Ethernet is a family of wired LAN technologies and standards defining frame formats, addressing, and communication over Ethernet links.

**Important points:** Ethernet frames use source/destination MAC addresses (not IP addresses) to deliver data within a LAN; modern Ethernet uses switches instead of a truly shared bus.

### 77. MAC Address Table

**Definition:** A table maintained by a switch (38), mapping which MAC address is reachable via which physical port.

**How it works:** When a switch receives a frame, it learns the sender's MAC address and port, and stores it. For future frames, it looks up the destination MAC in this table to forward directly to the correct port instead of broadcasting to all ports.

### 78. ARP (Address Resolution Protocol)

**Definition:** ARP resolves an IPv4 address to a MAC address within a local network.

**Why it is needed:** Applications communicate using IP addresses, but actual delivery within a LAN happens at the Data Link layer using MAC addresses — ARP is the bridge between the two.

**Related concepts:** ARP Request (79), ARP Reply (80), ARP Cache (81).

### 79. ARP Request

**Definition:** A **broadcast** message sent by a device asking "Who has this IP address? Tell me your MAC address," sent to all devices on the LAN.

### 80. ARP Reply

**Definition:** A **unicast** response sent by the device that owns the requested IP address, containing its MAC address.

**Full ARP example — step by step:**

```
1. Device A (192.168.1.10) wants to send data to Device B (192.168.1.20),
   but only knows B's IP address, not its MAC address.

2. Device A broadcasts an ARP Request to the whole LAN:
   "Who has 192.168.1.20? Tell 192.168.1.10 (MAC: AA:AA:AA:AA:AA:AA)"

3. Every device on the LAN receives the broadcast, but only
   Device B (192.168.1.20) recognizes its own IP and replies.

4. Device B sends an ARP Reply directly (unicast) to Device A:
   "192.168.1.20 is at MAC BB:BB:BB:BB:BB:BB"

5. Device A now has B's MAC address and can send frames directly to it.
   Device A also stores this mapping in its ARP Cache for future use.
```

### 81. ARP Cache

**Definition:** A temporary local table on each device storing recently resolved IP-to-MAC mappings, so ARP requests don't need to be repeated for every single packet.

**Important points:** ARP cache entries expire after a timeout period, after which a fresh ARP request is needed.

### 82. Unicast

**Definition:** Communication from one sender to exactly one specific receiver.

**Example:** A normal web page request/response between your browser and a server.

### 83. Broadcast

**Definition:** Communication from one sender to **all** devices on a network segment.

**Example:** An ARP Request; DHCP discovery messages.

### 84. Multicast

**Definition:** Communication from one sender to a specific **group** of interested receivers (not all, not just one).

**Example:** Video conferencing/streaming to a subscribed group; uses Class D addresses (57).

**Comparison — Unicast vs Broadcast vs Multicast:**

| Type | Recipients | Example |
|---|---|---|
| Unicast | One specific device | Normal web browsing |
| Broadcast | All devices on the LAN | ARP request |
| Multicast | A specific interested group | Group video streaming |

## Part 7 — OSI Model

### 85. OSI Model

**Definition:** The Open Systems Interconnection Model — a **theoretical/conceptual** 7-layer framework describing how data communication should be organized, published by ISO.

**What it means:** It is not a protocol itself, but a reference model that standardizes how different networking protocols and devices *should* interact, layer by layer, so that any two systems can communicate regardless of their underlying hardware/software.

**Why it is needed:** Breaks the complex problem of "how do two devices communicate" into 7 smaller, manageable, independent problems — each layer only needs to know how to talk to the layer directly above and below it.

**The 7 layers (top to bottom):**

- **Layer 7 — Application**
- **Layer 6 — Presentation**
- **Layer 5 — Session**
- **Layer 4 — Transport**
- **Layer 3 — Network**
- **Layer 2 — Data Link**
- **Layer 1 — Physical**

**Important points:** End devices (client, server) implement all 7 layers; a traditional IP router primarily operates at Layers 1–3 (Physical, Data Link, Network) for its core job of forwarding packets, since packet forwarding decisions don't require understanding application data.

**Related concepts:** TCP/IP Model (131), Encapsulation (18).

### 86. Physical Layer (Layer 1)

**Main responsibility:** Transmission of raw, unstructured bits (0s and 1s) over a physical medium — cables, radio waves, or light pulses.

**Data unit:** Bit

**Addressing:** None.

**Common concerns:** Cable/connector types, voltage levels, radio frequencies, encoding schemes (how bits are represented as signals), data rate, physical topology.

**Devices:** Hubs (37), repeaters (40), cables, NICs (physical layer part).

**Practical example:** The electrical pulses traveling through an Ethernet cable, or the radio waves carrying your Wi-Fi signal.

### 87. Data Link Layer (Layer 2)

**Main responsibility:** Reliable node-to-node (hop-to-hop) delivery of frames across a single physical/local link, plus error detection.

**Data unit:** Frame (17)

**Addressing:** MAC Address (71)

**Common concerns/functions:** Framing (93), error detection (95), flow control (97), access control (98/access to shared medium).

**Devices:** Switches (38), bridges (39), NICs (Data Link part).

**Practical example:** A switch reading the destination MAC address of a frame to decide which port to forward it out of.

**Related concepts:** See Part 8 for a deeper look at Data Link layer functions.

### 88. Network Layer (Layer 3)

**Main responsibility:** Logical addressing and routing — getting a packet from the source host to the destination host, potentially across many intermediate networks.

**Data unit:** Packet (14) / Datagram (16)

**Addressing:** IP Address (46)

**Common protocols:** IP, ICMP (111).

**Devices:** Routers (41).

**Practical example:** A router examining a packet's destination IP address and forwarding it toward the next network on the path.

**Related concepts:** See Part 9 for a deeper look at Network layer functions (routing, fragmentation, ICMP).

### 89. Transport Layer (Layer 4)

**Main responsibility:** End-to-end communication between applications on the source and destination hosts — includes segmentation, reliability (if using TCP), and multiplexing multiple app connections via port numbers.

**Data unit:** Segment (15)

**Addressing:** Port Number (115)

**Common protocols:** TCP (119), UDP (120).

**Practical example:** Your browser's connection to a web server is identified by a (source IP, source port, destination IP, destination port) tuple, managed at this layer.

**Related concepts:** See Part 10 for a full deep dive into the Transport layer (TCP, UDP, handshake, flow/congestion control).

### 90. Session Layer (Layer 5)

**Main responsibility:** Establishing, managing, and terminating "sessions" (a persistent logical connection/conversation) between two applications, including synchronization checkpoints.

**Key functions (core Session Layer responsibilities):**

- **Session establishment** — opening a dialogue between two applications.
- **Session maintenance/management** — keeping the dialogue active and organized while data is exchanged.
- **Session termination** — closing the dialogue cleanly once communication is finished.
- **Synchronization / checkpoints** — inserting sync points into a long data transfer so that, if interrupted, transfer can resume from the last checkpoint instead of starting over.

**Important distinction:** Authentication/authorization (verifying identity and permissions) and session hijacking (an attack where someone steals/reuses a valid session identifier) are security concepts that are *related* to the idea of a "session," but they are not themselves core OSI Session Layer responsibilities — they are typically implemented and discussed at the application level (see Part 17, Browser & Web Security, for cookies/sessions/session management in the web-development sense).

**Summary:** The Session Layer manages sessions, synchronization, and checkpoints in the OSI reference model. Note that the modern TCP/IP stack does not implement a distinct Session-layer protocol of its own — concepts like login sessions, cookies, and tokens are handled at the application level in practice, and are covered separately in Part 17 (Browser & Web Security).

### 91. Presentation Layer (Layer 6)

**Main responsibility:** Translating/formatting data between the application format and a common network format — the layer concerned with *how* data looks, not what it means.

**Key functions:**

- **Data translation** — converting between different character encodings (e.g., ASCII/Unicode/UTF-8) or data formats so both ends understand the data the same way.
- **Encryption/Decryption** — securing data before it's sent (e.g., TLS operates conceptually near this layer).
- **Compression** — reducing data size before transmission to save bandwidth.

**Practical example:** TLS/SSL encryption of an HTTPS connection conceptually mapped to the Presentation Layer (though in practice it's implemented as a layer sitting between Transport and Application in the real TCP/IP stack).

### 92. Application Layer (Layer 7)

**Main responsibility:** The layer that directly interacts with end-user software, providing network services the applications actually use.

**Common protocols:** HTTP/HTTPS (142/143), FTP (144), SMTP (145), SSH (146), DNS (140).

**Practical example:** When you open a browser and type a URL, the browser uses HTTP/HTTPS at this layer to request the web page.

**Important points:** "Application layer" refers to network-facing protocols, not the user-facing app itself — the browser is the application; HTTP is the Application-layer protocol it uses.

### The Complete Journey of Data Through All 7 Layers

**Sender side (Encapsulation — see 18 for the general concept):**

```
7. Application  : User writes an email / loads a webpage (raw data)
6. Presentation : Data encoded/compressed/encrypted if needed
5. Session      : Session established/tracked (e.g., login session)
4. Transport    : Data broken into Segments, port numbers added (TCP/UDP header)
3. Network      : Segment wrapped into a Packet, source/destination IP added
2. Data Link    : Packet wrapped into a Frame, source/destination MAC added
1. Physical     : Frame converted into bits -> electrical/light/radio signals
```

**Receiver side (Decapsulation — see 19):** the process runs in exact reverse — Physical layer receives raw bits, Data Link layer strips the frame header to get the packet, Network layer strips the IP header to get the segment, Transport layer strips the TCP/UDP header and reassembles the data, and finally the Application layer hands the original data to the receiving application.

**Practical example:** See Part 19, Example 1 ("What happens when I type `https://google.com`?") for a complete real-world walkthrough tying all 7 layers together.

## Part 8 — Data Link Layer (Deep Dive)

*(General Data Link layer role is covered in 87; this section covers its specific functions in more depth.)*

### 93. Framing

**Definition:** The process of organizing a stream of bits into distinct, well-defined units called frames, so the receiver knows exactly where one frame ends and the next begins.

**How it works:** Framing adds a header (with source/destination MAC address) and a trailer (with error-checking data) around the Network-layer packet. Special bit patterns or length fields mark the frame's boundaries, effectively signaling "data is coming" and "data has ended" to the receiving device.

**Example:** An Ethernet frame includes a preamble (signals the start of a frame), destination MAC, source MAC, a type/length field, the payload (the IP packet), and a trailing checksum (FCS) for error detection.

### 94. MAC Addressing

A data-link frame carries source and destination MAC addresses around the network-layer packet, so the frame can be delivered correctly within the local network segment (hop-to-hop delivery). See **MAC Address (71)** for the full explanation of the address itself.

### 95. Error Detection

**Definition:** Techniques used to detect whether data was corrupted during transmission (e.g., due to noise/interference).

**Common technique:** A **checksum/CRC (Cyclic Redundancy Check)** is calculated from the frame's data before sending and appended as a trailer. The receiver recalculates it on arrival — if the two don't match, the frame is discarded/considered corrupted.

**Important points:** CRC and checksums can detect data corruption; they do not themselves correct the error — recovery (if needed) is left to a higher layer, typically via retransmission (see 96, 127).

### 96. Error Correction

**Definition:** Techniques that not only detect an error but can also fix it without needing retransmission (e.g., Hamming code, Forward Error Correction).

**Important points:** Error correction adds redundancy proactively (more overhead), whereas error detection + retransmission (used by TCP, see 127) fixes errors reactively, only when needed — the Data Link layer typically only *detects* errors and discards bad frames, leaving retransmission to higher layers (like TCP).

### 97. Flow Control (Data Link layer)

**Definition:** A mechanism to ensure a fast sender does not overwhelm a slow receiver, by regulating the rate/amount of data sent.

**Important points:** Flow control exists at *both* the Data Link layer (link-level, hop-to-hop, e.g., pause frames) *and* the Transport layer (end-to-end, e.g., TCP's sliding window — see 128). Don't confuse the two: Data Link flow control manages a single physical link; Transport-layer flow control manages the whole end-to-end connection.

### 98. Access Control

**Definition:** Rules governing how devices sharing the same physical medium (e.g., a wireless channel, or old shared-bus Ethernet) take turns transmitting, to avoid or manage collisions.

**Related concepts:** Collision (99), CSMA/CD (100), CSMA/CA (101).

### 99. Collision

**Definition:** A collision occurs when two devices transmit at the same time on a shared medium, causing their signals to interfere.

**Important points:** Collisions were common on old shared-bus/hub-based networks; modern switch-based Ethernet largely eliminates them (each switch port is its own collision domain), though Wi-Fi (a genuinely shared medium) still needs collision-avoidance mechanisms.

### 100. CSMA/CD (Carrier Sense Multiple Access with Collision Detection)

**Definition:** CSMA/CD is a historical/shared-medium Ethernet mechanism where a device listens to the medium before transmitting, and if a collision is detected during transmission, both devices stop, wait a random time, and retry.

**How it works:** "Carrier Sense" = listen before talking; "Collision Detection" = keep listening while talking, and if a collision is heard, stop and back off randomly before retrying.

**Important points:** Modern switched, full-duplex Ethernet normally does not experience collisions at all (each switch port is its own collision domain, and sending/receiving happen on separate paths), so CSMA/CD is largely a legacy mechanism from the shared/half-duplex Ethernet era rather than something active on typical modern networks.

### 101. CSMA/CA (Carrier Sense Multiple Access with Collision Avoidance)

**Definition:** CSMA/CA is a Wi-Fi access mechanism that attempts to reduce the probability of collisions before transmission, rather than detecting them after the fact.

**How it works:** A device listens for a clear channel, and if busy, waits a random backoff period. It may also use a request-to-send/clear-to-send (RTS/CTS) handshake before transmitting. Since wireless devices often can't reliably "hear" a collision while transmitting (unlike wired CSMA/CD), avoidance is preferred over detection.

**Comparison — CSMA/CD vs CSMA/CA:**

| Aspect | CSMA/CD | CSMA/CA |
|---|---|---|
| Medium | Wired (shared Ethernet) | Wireless (Wi-Fi) |
| Strategy | Detect collision, then recover | Avoid collision before it happens |
| Used today | Rarely (switches eliminated need) | Yes, actively in Wi-Fi |

### Flow Control vs Congestion Control — Important Distinction

These two are frequently confused; keep them separate:

| Aspect | Flow Control | Congestion Control |
|---|---|---|
| Concerned with | Receiver's capacity | Network's capacity |
| Goal | Don't overwhelm the *receiver* | Don't overwhelm the *network* (routers/links) |
| Where | Data Link layer (per hop) and Transport layer (end-to-end) | Transport layer (end-to-end) |
| Mechanism example | TCP sliding window (receiver-advertised) | TCP congestion window (slow start, etc.) |

See **129. Congestion Control** in Part 10 for the full Transport-layer treatment.

## Part 9 — Network Layer (Deep Dive)

*(General Network layer role is covered in 88; this section, along with Part 14 - Routing, covers its functions in depth.)*

### 102. Network Layer

See **88. Network Layer** for the core definition. This section covers its supporting concepts in more detail.

### 103. Logical Addressing

**Definition:** Addressing based on a device's *position in the network* (its IP address) rather than its fixed hardware identity (MAC address) — "logical" because the same physical device can be assigned a different IP depending on which network it joins.

**Related concepts:** IP Address (46).

### 104. Routing

See **Part 14 — Routing** for the complete dedicated treatment of this topic (why it's needed, routing tables, static vs dynamic routing, and a full packet-journey example).

### 105. Routing Table

**Definition:** A table stored on a router (or host) listing known destination networks and which "next hop"/interface to use to reach each of them.

**Typical fields:** Destination network, subnet mask, next hop IP, outgoing interface, metric/cost.

**Related concepts:** Next Hop (106), Default Gateway (107).

### 106. Next Hop

**Definition:** The very next router (or the destination itself, if directly reachable) that a packet should be forwarded to, on its way toward its final destination.

### 107. Default Gateway

**Definition:** The router that a device sends traffic to the default gateway is the next-hop router used when the host's routing table has no more specific route for the destination — for most home/office devices, this is simply "the router."

**Example:** Your laptop (`192.168.1.10`) wants to reach `google.com`'s server. Since that server isn't on your local `192.168.1.0/24` network, your laptop sends the packet to its default gateway (e.g., `192.168.1.1` — your router), which then forwards it onward toward the Internet.

### 108. Packet Forwarding

**Definition:** The core job of a router — receiving a packet, checking its destination IP against the routing table, and sending it out the correct interface toward the next hop.

**Related concepts:** See Part 14 for a full step-by-step forwarding example across multiple routers.

### 109. Fragmentation

**Definition:** The process of breaking a large packet into smaller pieces so it can pass through a network link that only supports a smaller maximum packet size (MTU — Maximum Transmission Unit).

**Why it is needed:** Different network links (Ethernet, Wi-Fi, older technologies) support different maximum packet sizes; fragmentation lets a large packet still cross a link with a smaller limit.

**IPv4 vs IPv6 — an important distinction:**

- **In IPv4**, both the original sending host *and* intermediate routers along the path are allowed to fragment a packet if it's too large for the next link's MTU.
- **In IPv6**, routers do **not** fragment packets in transit. If a packet is too large for a link, the router instead drops it and sends back an ICMP "Packet Too Big" message; only the **source host** performs fragmentation in IPv6, and only before sending, based on what it knows (or discovers) about the path's MTU.
- This shift is one of the deliberate design changes in IPv6 — moving the fragmentation burden away from routers (which slows them down) and onto the sending host.

**Related concepts:** **Path MTU Discovery (PMTUD)** — a technique where a sending host discovers the smallest MTU along the entire path to a destination *before* sending large packets (by sending packets with a "don't fragment" flag and reacting to any "too big" errors it gets back), so it can size its packets to avoid needing fragmentation at all. This is especially important in IPv6, where the source is responsible for fragmentation and benefits from knowing the right size upfront.

### 110. Reassembly

**Definition:** The process of putting fragmented packet pieces back together into the original packet at the receiving end, using fragment offset/identification fields in the IP header.

**Important points:** Fragmentation/reassembly adds overhead and potential points of failure (a single lost fragment means the whole packet must be resent), which is why modern networks try to avoid it where possible — e.g., via Path MTU Discovery (see above), which finds a safe packet size upfront instead of relying on fragmentation.

### 111. ICMP (Internet Control Message Protocol)

**Definition:** A Network-layer protocol used for sending diagnostic and error-reporting messages between devices — not used to carry actual application data, but to report problems (e.g., "destination unreachable") or perform diagnostics (e.g., `ping`).

**Example:** The `ping` command sends ICMP "Echo Request" messages and listens for "Echo Reply" messages to test reachability and measure latency (12) to another device.

**Important points:** `ping` and `tracert`/`traceroute` use ICMP differently: **Windows `tracert`** sends ICMP Echo Request messages (like an extended `ping`) with increasing TTL values. **Traditional Unix/Linux `traceroute`** commonly sends UDP probes to a high, likely-unused port instead — though many modern implementations can also be run in an ICMP mode (`traceroute -I`) or a TCP mode (`traceroute -T`). What's common across all of them is the *mechanism*, not necessarily the probe protocol: see TTL (112) for how intermediate routers get triggered to reveal themselves regardless of which probe type is used.

### 112. TTL (Time To Live)

**Definition:** A field in the IP header that limits how many router hops a packet can pass through before it's discarded — decremented by 1 at every router it passes.

**Why it is needed:** Prevents packets from looping forever in the network (e.g., due to a routing misconfiguration) — once TTL reaches 0, the packet is dropped and the router sends back an ICMP "Time Exceeded" message.

**Example:** `traceroute`/`tracert` deliberately sends probes with increasing TTL values (1, 2, 3...) — each router along the path that decrements TTL to 0 sends back an ICMP "Time Exceeded" message (111) identifying itself, regardless of whether the original probe was ICMP, UDP, or TCP. This is how the tool maps the full route hop by hop.

### 113. Unicast / Multicast / Broadcast Routing

See **82 (Unicast), 83 (Broadcast), 84 (Multicast)** in Part 6 for the full definitions — at the routing/network layer, these same concepts determine whether a router needs to forward a packet to one specific destination, replicate it to a defined group, or (for broadcast, which is typically restricted to a local subnet) deliver it to every host on the local network.

## Part 10 — Transport Layer

### 114. Transport Layer

See **89. Transport Layer** for the core definition. This section is a full deep dive into its functions.

### 115. Port Numbers

**Definition:** A 16-bit number (range 0–65535) used to identify a specific application/process on a device, allowing multiple network conversations to happen simultaneously on one IP address.

**Why it is needed:** An IP address identifies the *device*; a port number identifies the *specific application/service* on that device (e.g., web server vs. email server running on the same machine).

**Example:** A single server with IP `93.184.216.34` can run a web server on port 443 and a mail server on port 25 at the same time — both reachable at the same IP but distinguished by port.

**Related concepts:** Well-Known Ports (116), Registered Ports (117), Dynamic/Private Ports (118).

### 116. Well-Known Ports (0–1023)

**Definition:** Reserved by IANA for standard, widely-used services.

| Port | Service |
|---|---|
| 20/21 | FTP |
| 22 | SSH |
| 25 | SMTP |
| 53 | DNS |
| 80 | HTTP |
| 443 | HTTPS |

### 117. Registered Ports (1024–49151)

**Definition:** Assigned by IANA to specific applications/services that are widely used but not considered "core" internet standards; software vendors can register a port for their own applications.

### 118. Dynamic / Private Ports (49152–65535)

**Definition:** Not reserved for any specific service — used dynamically, usually as the temporary **source** port chosen by a client's operating system for outgoing connections.

**Example:** When your browser connects to a website on port 443, your OS picks a random dynamic port (e.g., 51342) as the *source* port for that specific connection.

### 119. TCP (Transmission Control Protocol)

**Definition:** A **connection-oriented** Transport-layer protocol that provides reliable, ordered delivery using acknowledgements, sequence numbers, retransmission, and error detection.

**Why it is needed:** Many applications (web pages, file transfers, email) cannot tolerate lost or out-of-order data — TCP is designed so that, under normal conditions, data arrives completely and in the correct order, or the application is informed of failure. (No transport protocol can guarantee success under every possible network failure — e.g., a sufficiently long, total loss of connectivity will still cause a TCP connection to fail.)

**Key features (benefits):** Reliable delivery (retransmits lost data), correct ordering (via sequence numbers), flow control, congestion control, error checking.

**Related concepts:** Three-Way Handshake (122), Sequence Numbers (125), Acknowledgements (126).

### 120. UDP (User Datagram Protocol)

**Definition:** A **connectionless**, lightweight Transport-layer protocol that sends data ("datagrams") without establishing a connection first. UDP does not provide retransmission, ordering, or delivery guarantees — it includes a checksum field for detecting corruption, but does not act on a failed checksum beyond dropping the datagram (no automatic recovery).

**Why it is needed:** Some applications (live video, gaming, DNS lookups) value **speed** over guaranteed delivery — retransmitting a lost video frame from a second ago is often more disruptive than simply skipping it. UDP has lower protocol overhead than TCP, but actual performance depends on the network conditions and how the application uses the protocol.

### 121. TCP vs UDP

| Feature | TCP | UDP |
|---|---|---|
| Connection | Connection-oriented (three-way handshake) | Connectionless (no handshake) |
| Reliability | Reliable, ordered delivery via acknowledgements, sequence numbers, retransmission | No built-in delivery or ordering guarantees |
| Ordering | Ensures correct packet order | No ordering guaranteed |
| Error checking | Checksum + acknowledgement-driven retransmission | Checksum only, no retransmission |
| Flow/Congestion control | Yes | No |
| Overhead | Higher — connection setup, acknowledgements, retransmission logic | Lower — no connection setup or acknowledgement tracking |
| Data unit | Segment | Datagram |
| Common use cases | Web browsing, email, file transfer | Streaming, gaming, DNS, VoIP |

**Important points:** TCP's reliability mechanisms add overhead (connection setup, acknowledgements, potential retransmission), while UDP's lack of these mechanisms means less overhead per packet — but actual observed performance for a given application depends heavily on network conditions (loss, congestion) and how the application itself is implemented, not just the protocol in isolation.

**Rule of thumb — when to use which:** Use TCP when correctness/completeness matters more than minimizing overhead (e.g., file downloads, bank transactions). Use UDP when low overhead/latency matters more than guaranteed delivery of every packet (e.g., live video calls, multiplayer games, DNS lookups where a quick retry is cheap).

### 122. TCP Three-Way Handshake

**Definition:** The process TCP uses to establish a reliable connection between client and server *before* any actual data is exchanged.

**How it works, step by step:**

```
Client                                   Server
  |------------ SYN (seq=x) ------------->|   1. Client: "I want to connect, my starting sequence number is x"
  |<-------- SYN-ACK (seq=y, ack=x+1) ----|   2. Server: "OK, acknowledged. My starting sequence number is y"
  |------------ ACK (ack=y+1) ----------->|   3. Client: "Acknowledged. Connection established."

           -- connection now OPEN, data can flow --
```

**Why 3 steps:** The exchange synchronizes initial sequence numbers (125) in both directions and confirms that both sides are ready for bidirectional communication — a 2-way handshake would only confirm and synchronize one direction.

### 123. TCP Connection Termination

**Definition:** The process of gracefully closing a TCP connection, typically using a four-step exchange (sometimes called the "four-way handshake" / FIN-ACK sequence).

**How it works, step by step:**

```
Client                                   Server
  |------------- FIN -------------------->|   1. Client: "I'm done sending data"
  |<------------ ACK ---------------------|   2. Server: "Acknowledged"
  |<------------ FIN ---------------------|   3. Server: "I'm also done sending"
  |------------- ACK -------------------->|   4. Client: "Acknowledged. Connection closed."
```

### 124. Reliability

**Definition:** TCP provides reliable, ordered delivery using acknowledgements, sequence numbers, retransmission, and error detection — under normal network conditions, data arrives complete and in order, or the failure is surfaced to the application.

### 125. Sequence Numbers

**Definition:** A number assigned to each byte of data in a TCP segment, letting the receiver reorder segments that arrive out of order and detect missing data.

### 126. Acknowledgements (ACK)

**Definition:** A signal sent back by the receiver confirming that specific data has been successfully received (referencing the sequence number of the next byte expected).

### 127. Retransmission

**Definition:** If the sender doesn't receive an acknowledgement within an expected time, it assumes the data was lost and resends it.

### 128. Flow Control (Transport layer)

**Definition:** TCP's mechanism to prevent a fast sender from overwhelming a slower receiver, using a "sliding window" — the receiver advertises how much data (buffer space) it can currently accept, and the sender limits itself accordingly.

**Important points:** This is end-to-end (sender-to-receiver across the whole connection), different from Data Link-layer flow control (97), which is per-hop.

### 129. Congestion Control

**Definition:** TCP's mechanism to prevent overwhelming the **network** (routers, links) — separate from flow control, which protects the *receiver*.

**How it works (basic idea):** TCP starts sending slowly ("slow start"), gradually increases its sending rate, and backs off sharply if it detects packet loss (a sign of network congestion) — cyclically probing for the network's available capacity.

**Important points:** Flow control asks "can the *receiver* handle more?"; congestion control asks "can the *network path* handle more?" — see the comparison table in Part 8 for a side-by-side.

### 130. Error Control

**Definition:** TCP's overall mechanism for detecting and recovering from errors — implemented through checksums (to detect corruption) combined with acknowledgements and retransmission (to recover from loss/corruption).

## Part 11 — TCP/IP Model

### 131. TCP/IP Model

**Definition:** The **practical, implemented** 4-layer networking model that the real-world Internet actually runs on (as opposed to OSI, which is a theoretical 7-layer reference model).

**The 4 layers (top to bottom):**

- **Layer 4 — Application Layer**
- **Layer 3 — Transport Layer**
- **Layer 2 — Internet / Network Layer**
- **Layer 1 — Network Access Layer** (also called Link Layer)

### 132. Application Layer (TCP/IP)

**Definition:** Combines the responsibilities of the OSI Application, Presentation, and Session layers (92, 91, 90) into one layer.

**Common protocols:** HTTP/HTTPS, DNS, FTP, SMTP, SSH — see Part 12 for details.

### 133. Transport Layer (TCP/IP)

**Definition:** Functionally identical to the OSI Transport layer (89) — handles TCP/UDP, ports, segmentation, and (for TCP) reliability.

### 134. Internet / Network Layer (TCP/IP)

**Definition:** Functionally identical to the OSI Network layer (88) — handles IP addressing and routing.

### 135. Network Access Layer (TCP/IP)

**Definition:** Combines the responsibilities of the OSI Data Link and Physical layers (87, 86) into one layer — handles MAC addressing, framing, and the actual physical transmission of bits.

### 136. OSI vs TCP/IP

| Aspect | OSI Model | TCP/IP Model |
|---|---|---|
| Nature | Theoretical/reference model | Practical, actually implemented |
| Layers | 7 | 4 |
| Developed by | ISO | DARPA / Internet pioneers |
| Used for | Teaching/conceptual understanding | The real Internet runs on this |

### 137. OSI-to-TCP/IP Layer Mapping

```
OSI (7 layers)                TCP/IP (4 layers)
--------------------------------------------------
7. Application     \
6. Presentation      >----->  4. Application
5. Session          /

4. Transport        ------->  3. Transport

3. Network          ------->  2. Internet / Network

2. Data Link        \
                       >----->  1. Network Access
1. Physical         /
```

### 138. Encapsulation in TCP/IP

**Definition:** The same encapsulation concept explained in **18** (headers added while going down the layers), simply mapped onto TCP/IP's 4 layers instead of OSI's 7:

```
Application data
 -> [TCP/UDP Header | Data]                       (Transport layer)
 -> [IP Header | TCP/UDP Header | Data]            (Internet layer)
 -> [Frame Header | IP Header | ... | Frame Trailer]  (Network Access layer)
 -> bits on the wire/air
```

### 139. Decapsulation in TCP/IP

**Definition:** The reverse of 138 — same concept as OSI decapsulation (19), applied to the 4-layer TCP/IP stack as data moves up from Network Access → Internet → Transport → Application at the receiving device.

## Part 12 — Important Network Protocols

*(This section gives a quick-reference overview of each protocol. DNS gets a full dedicated deep dive in Part 13, since it's a large enough topic to deserve its own space.)*

### 140. DNS (Domain Name System)

**Purpose:** Translates human-friendly domain names (e.g., `google.com`) into IP addresses that computers actually use to route traffic.
**Port:** Traditional DNS uses port 53 over UDP and TCP. DNS can also be transported through protocols such as DNS over TLS (DoT) and DNS over HTTPS (DoH).
**Full explanation:** See **Part 13 — DNS**.

### 141. DHCP (Dynamic Host Configuration Protocol)

**Definition:** A protocol that automatically assigns IP addresses (and other network configuration — subnet mask, default gateway, DNS server) to devices when they join a network.

**How it works (DORA process):**

```
1. Discover : Client broadcasts "Is there a DHCP server? I need an IP address"
2. Offer    : DHCP server responds, offering an available IP address
3. Request  : Client requests to use that specific offered IP address
4. Ack      : Server confirms/finalizes the assignment (a "lease")
```

**Port:** 67 (server), 68 (client), UDP.

**Related concepts:** Dynamic IP Address (52).

### 142. HTTP (HyperText Transfer Protocol)

**Definition:** The protocol used to request and transfer web pages/resources between a browser (client) and a web server.
**Port:** 80. **Transport:** TCP.
**Important points:** Sends data in plain text — not encrypted, so it's vulnerable to eavesdropping/tampering.
**Full explanation:** See **Part 16 — HTTP In Depth** for request/response structure, methods, headers, status codes, and persistent connections — essential for Web Development.

### 143. HTTPS (HTTP Secure)

**Definition:** HTTP layered on top of TLS/SSL encryption, so all data exchanged between browser and server is encrypted and tamper-protected.
**Port:** 443. **Transport:** TCP.
**Related concepts:** See Part 15 for a full comparison of HTTP vs HTTPS and how TLS works, and Part 16 for HTTP's request/response mechanics (which apply equally to HTTPS).

### 144. FTP (File Transfer Protocol)

**Definition:** A protocol specifically designed for transferring files between a client and a server.
**Ports:** 20 (data), 21 (control). **Transport:** TCP.
**Important points:** Classic FTP is unencrypted; secure variants (SFTP, FTPS) add encryption.

### 145. SMTP (Simple Mail Transfer Protocol)

**Definition:** The protocol used to **send** email from a client to a mail server, or between mail servers.
**Port:** 25 (also 587 for authenticated client submission). **Transport:** TCP.
**Important points:** SMTP is only for *sending*; retrieving email uses separate protocols (like IMAP/POP3), which fall outside this document's core scope but are useful to know exist.

### 146. SSH (Secure Shell)

**Definition:** A protocol for securely accessing and controlling a remote device's command line/system over an encrypted connection.
**Port:** 22. **Transport:** TCP.
**Use case:** Remotely administering servers, secure file transfer (via SFTP, which runs over SSH).

### 147. ICMP (Internet Control Message Protocol)

See **111. ICMP** in Part 9 for the full explanation — used for diagnostics/error-reporting (e.g., `ping`, `traceroute`), not for carrying application data.

### 148. TCP

See **119. TCP** in Part 10 for the full explanation.

### 149. UDP

See **120. UDP** in Part 10 for the full explanation.

**Protocol quick-reference table:**

| Protocol | Port | Transport | Purpose |
|---|---|---|---|
| DNS | 53 | UDP/TCP | Domain name → IP resolution |
| DHCP | 67/68 | UDP | Automatic IP configuration |
| HTTP | 80 | TCP | Unencrypted web traffic |
| HTTPS | 443 | TCP | Encrypted web traffic |
| FTP | 20/21 | TCP | File transfer |
| SMTP | 25/587 | TCP | Sending email |
| SSH | 22 | TCP | Secure remote access |
| ICMP | — (no port) | — (own IP-layer protocol) | Diagnostics/errors |

## Part 13 — DNS (Deep Dive)

DNS is important enough to deserve its own dedicated, detailed section beyond the quick-reference entry in Part 12.

### What DNS Is and Why It Exists

Computers route traffic using IP addresses (46), but IP addresses (e.g., `142.250.183.14`) are hard for humans to remember. DNS is essentially the Internet's "phonebook" — it lets you type a memorable **domain name** (like `google.com`) and transparently translates it to the correct IP address behind the scenes.

### Domain Name

**Definition:** A human-readable address for a website/service (e.g., `www.google.com`), structured hierarchically from right to left:

```
www . google . com
 |       |      |
 |       |      +-- Top-Level Domain (TLD)
 |       +--------- Second-level domain (the organization's name)
 +----------------- Subdomain (e.g., "www")
```

### The DNS Hierarchy

#### Root DNS Servers

**Definition:** The top of the DNS hierarchy — there are only **13 logical root server addresses** in the world (each backed by many physical, geographically distributed servers via anycast). They don't know the final IP address of a domain, but they know which TLD server to ask next.

#### TLD (Top-Level Domain) Servers

**Definition:** Servers responsible for a specific domain suffix/extension — e.g., `.com`, `.org`, `.in`, `.net`. They direct queries to the correct Authoritative server for the specific domain.

#### Authoritative DNS Servers

**Definition:** The server that actually holds the final DNS records for a specific domain — the authoritative server returns the requested DNS record, such as an A record containing an IPv4 address (see DNS Records below), for that domain.

#### DNS Resolver

**Definition:** The server (typically run by your ISP, or a public resolver like Google's `8.8.8.8` or Cloudflare's `1.1.1.1`) that does the actual multi-step lookup work on your behalf, then caches the result for future queries.

### DNS Resolution — Full Step-by-Step Example

**Scenario:** You type `www.example.com` into your browser for the first time. (The IP address used below, `93.184.216.34`, is an example value for illustration — the actual address for any given domain is whatever its current DNS A record specifies.)

```
1. Browser checks its own cache -> not found.
2. OS checks its local DNS cache -> not found.
3. Request goes to the configured DNS Resolver (e.g., your ISP's resolver).
4. Resolver has no cached answer, so it starts a fresh lookup:

   a. Resolver asks a ROOT server: "Where do I find .com domains?"
      Root server replies: "Ask this .com TLD server."

   b. Resolver asks the .com TLD server: "Where is example.com?"
      TLD server replies: "Ask this Authoritative server for example.com."

   c. Resolver asks the Authoritative server: "What is the IP for www.example.com?"
      Authoritative server replies with the requested record - e.g. an A record
      containing the (example) IPv4 address "93.184.216.34"

5. Resolver sends the example address 93.184.216.34 back to your browser, and
   caches this answer for a period of time (defined by the record's TTL).

6. Browser now opens a TCP connection (and TLS handshake, if HTTPS)
   directly to that address to actually request the web page.
```

### DNS Caching

**Definition:** Storing a previously resolved domain→IP mapping temporarily (at the browser, OS, or resolver level) so repeated lookups for the same domain don't need to repeat the full hierarchy walk every time — dramatically speeding up subsequent visits.

**Important points:** Each DNS record has a **TTL (Time To Live)** value specifying how long it can be safely cached before it should be looked up again.

### DNS Records

**Definition:** Entries stored on an authoritative DNS server, each mapping a domain name to a specific piece of information.

| Record | Purpose |
|---|---|
| **A** | Maps a domain name to an IPv4 address |
| **AAAA** | Maps a domain name to an IPv6 address |
| **CNAME** | Maps an alias domain name to another (canonical) domain name |
| **MX** | Specifies the mail server(s) responsible for receiving email for the domain |
| **NS** | Specifies the authoritative name server(s) for the domain |

**Example:** `example.com A 93.184.216.34` means "the domain `example.com` resolves to the (example) IPv4 address `93.184.216.34`" via its A record.

## Part 14 — Routing (Deep Dive)

### What Routing Is

**Definition:** Routing is the process of selecting a path across one or more networks for data to travel from its source to its destination, and the act of actually forwarding packets along that path, hop by hop.

### Why Routing Is Needed

A single device (host) only knows how to deliver data directly to devices on its *own* local network. Reaching a device on a *different* network (e.g., a server across the world) requires a chain of intermediate routers (41), each forwarding the packet one hop closer to its destination — routing is what makes this possible.

### Router, Routing Table, Next Hop, Default Route

These core building blocks are already defined in Part 9 (avoiding repetition, per the one-topic-one-place rule): see **Router (41)**, **Routing Table (105)**, **Next Hop (106)**, **Default Gateway (107)** — a "default route" is simply the routing-table entry that matches "everything else" and points to the default gateway.

### Packet Forwarding

See **Packet Forwarding (108)** — the router-level operation of looking up a destination in the routing table and sending the packet out the correct interface.

### Static Routing

**Definition:** Routes are manually configured by a network administrator and do not change unless someone updates them.

**Advantages:** Predictable, secure (no risk of malicious route announcements), low overhead — no protocol messages needed.

**Disadvantages:** Doesn't automatically adapt if a link fails; not practical for large/frequently-changing networks.

**Use case:** Small networks, or specific fixed routes (e.g., a single backup link) in larger networks.

### Dynamic Routing

**Definition:** Routers automatically discover and share information about network paths with each other using **routing protocols**, and adjust routes automatically if the network topology changes (e.g., a link goes down).

**Basic idea of routing protocols:** Routers periodically exchange information about which networks they can reach (and at what "cost," e.g., number of hops or link speed) with their neighboring routers. Over time, every router builds a more complete picture of the network and can calculate the preferred/best path to any destination according to the routing protocol's metrics and rules — and if a link fails, they detect this and recalculate automatically.

**Advantages:** Automatically adapts to failures/changes; scales much better for large networks.

**Disadvantages:** More overhead (constant protocol traffic between routers); more complex to configure/secure.

**Comparison — Static vs Dynamic Routing:**

| Aspect | Static Routing | Dynamic Routing |
|---|---|---|
| Configuration | Manual | Automatic (via routing protocols) |
| Adapts to failure | No | Yes |
| Overhead | Very low | Higher (protocol traffic) |
| Best for | Small/simple networks | Large/changing networks |

### Full Example: A Packet's Journey Through Multiple Routers

```
Your Laptop (192.168.1.10)
   |
   | Step 1: Destination (a server on the internet) is NOT on your local
   |         network, so the packet is sent to your Default Gateway (107)
   v
[Home Router] (NAT applied here - see 69)
   |
   | Step 2: Router checks its routing table, doesn't have a specific
   |         route, forwards via its own default route to the ISP
   v
[ISP Router 1] --- checks routing table, forwards to next hop
   |
   v
[ISP Router 2] --- checks routing table, forwards to next hop
   |
   v
[Backbone / Internet Exchange Routers] --- forward toward destination network
   |
   v
[Destination's Network Router] --- delivers packet to the final server
   |
   v
Destination Server (e.g., 93.184.216.34)
```

At each router, the same basic operation repeats: check the destination IP → look up the routing table → decrement TTL (112) by 1 → forward out the correct interface toward the next hop. This continues until the packet either reaches its destination or its TTL reaches zero and it's discarded.

## Part 15 — Security & Privacy

*(This section is explained technically and neutrally, for understanding how these systems work — not as a guide to bypassing security or accessing restricted content.)*

### 150. Encryption

**Definition:** The process of converting readable data (plaintext) into an unreadable, scrambled form (ciphertext) using a mathematical algorithm and a key, so that only someone with the correct key can read it.

### 151. Decryption

**Definition:** The reverse of encryption — converting ciphertext back into readable plaintext, using the correct key.

**How data travels while encrypted:** Data encrypted by a particular security protocol remains protected until it reaches the endpoint where that encryption is terminated and decrypted. Anyone intercepting the traffic in between sees only scrambled data, not the original content.

### 152. HTTP vs HTTPS

See **142 (HTTP)** and **143 (HTTPS)** for the base definitions.

| Aspect | HTTP | HTTPS |
|---|---|---|
| Encryption | None (plaintext) | TLS-encrypted |
| Port | 80 | 443 |
| What an eavesdropper (e.g., your ISP) can see | Everything, including page content | Cannot generally read the encrypted content, but may still observe or infer metadata such as destination IP addresses and, depending on DNS/TLS configuration, the domain name |

**Important points:** With HTTPS, an ISP generally cannot read the encrypted HTTP content — the actual pages viewed, form data, messages, etc. — but it may still observe or infer metadata such as which IP addresses you're connecting to, and, depending on DNS/TLS configuration (e.g., whether DNS queries and the TLS handshake's SNI field are also encrypted), the domain name you're visiting. Browsing in "incognito/private" mode does not hide this from your ISP at all — it only stops your *own browser* from saving local history/cookies; your ISP still sees the same network traffic either way.

### 153. TLS (Transport Layer Security)

**Definition:** The cryptographic protocol that actually implements the encryption behind HTTPS (and other secure protocols) — the modern, secure successor to the older SSL protocol.

**How it works (simplified):** When your browser connects to an HTTPS site, a "TLS handshake" occurs: the server proves its identity using a digital certificate, and both sides agree on encryption keys to use for the rest of the session — after this handshake, all subsequent data is encrypted.

### 154. VPN (Virtual Private Network)

**Definition:** A service that creates an encrypted "tunnel" between your device and a VPN server, routing traffic through that server, and masking your real IP address (from the perspective of destinations) for that traffic.

**Why it is needed:** Protects the traffic routed through it from being read by your local network/ISP, and lets that traffic appear to be coming from the VPN server's location/IP address instead of your own.

**How it works, step by step:**

```
Your Device --- [Encrypted VPN Tunnel] ---> VPN Server ---> Internet (destination website)
```

Traffic routed through the VPN tunnel is encrypted by your device and sent to the VPN server; the VPN server decrypts the *VPN tunnel's* encryption and forwards the traffic to the actual destination on your behalf (acting a bit like NAT/a proxy) — the destination website sees the VPN server's IP address, not yours. Whether this covers *all* of a device's traffic or only some of it depends on configuration: many VPN clients do route everything by default, but **split tunneling** (a common feature) lets specific apps or destinations bypass the VPN tunnel entirely, sending that traffic directly instead.

**Important points:** A VPN does not change the IP address assigned to your device/interface — your device still has its own local/public IP. Instead, Internet destinations generally see the VPN server's public IP as the source of traffic routed through the VPN, because the VPN server is the one actually talking to the destination on your behalf.

### 155. VPN Tunnel

**Definition:** The encrypted logical connection/path between your device and the VPN server. Traffic routed through the VPN travels through this encrypted tunnel; the exact traffic covered (e.g., all device traffic, or only specific apps) depends on the VPN configuration. Intermediate parties (your ISP, network operators between you and the VPN server) cannot read the contents of what passes through the tunnel.

### 156. VPN Server

**Definition:** The remote server operated by the VPN provider that terminates the VPN tunnel — it decrypts the *VPN tunnel's own encryption* on incoming traffic and forwards the underlying traffic on to the actual destination (and does the reverse for the response).

**Important points:** Decrypting the VPN tunnel is **not the same** as decrypting HTTPS/TLS. If you visit an HTTPS website through a VPN, there are two independent layers of encryption at that point: the VPN tunnel's encryption (between your device and the VPN server) and the website's own TLS encryption (between your browser and the destination server, see 153). The VPN server removes the *outer* VPN-tunnel layer to see where to forward the traffic, but the *inner* HTTPS/TLS-encrypted payload remains protected end-to-end between your browser and the actual destination server — the VPN server cannot read it.

### 157. ISP Visibility

**Definition:** What your Internet Service Provider can and cannot observe about your traffic.

**Without a VPN:** Your ISP can see which websites/servers you connect to (via DNS lookups and destination IPs), and — for unencrypted HTTP — potentially the actual content.

**With a VPN:** With a VPN, the ISP generally cannot read the encrypted VPN traffic or see the final HTTP content, but it may observe metadata such as the VPN server address, timing, and traffic volume.

**Important points:** A VPN doesn't eliminate visibility — it *shifts* it from your ISP to the VPN provider instead. The VPN provider can potentially observe traffic metadata and, for traffic it can decrypt, potentially inspect the content. What it retains depends on its configuration and logging practices — see VPN Logging (160).

### 158. Deep Packet Inspection (DPI)

**Definition:** A network monitoring technique where an ISP/network operator examines the actual content/metadata of packets passing through it (not just the header), to identify what kind of traffic it is, and potentially block or throttle specific types of traffic or services.

**Important points:** DPI is one of the tools ISPs/governments can use to detect and selectively block specific services — even sometimes able to detect and block VPN traffic itself, if configured to look for VPN protocol signatures.

### 159. Proxy vs VPN

| Aspect | Proxy | VPN |
|---|---|---|
| Scope | Typically operates at the application level — usually just one app/browser | Typically routes traffic for the whole device, though this depends on configuration |
| Encryption | Typically operates at the application level and may not encrypt traffic | Creates an encrypted tunnel for traffic routed through the VPN |
| Speed impact | Usually minimal | VPNs may add overhead or latency; actual impact depends on the VPN, network, and routing path |
| Purpose | Mainly IP/location masking for a specific app | IP masking + security/privacy for traffic routed through it |

**Important points:** Not every proxy is unencrypted, and not every VPN automatically covers literally every packet from every application — actual behavior depends on the specific proxy or VPN software and how it's configured.

### 160. VPN Logging

**Definition:** Whether and how much a VPN provider records about your activity (connection times, source IP, and sometimes even the destinations you visit).

**Important points:** A "no-log" VPN provider claims not to retain records that could identify what you did while connected — but this is a trust/policy claim, not something you can technically verify from outside; A "no-log" claim is a provider policy/trust claim; users generally cannot independently verify all logging behavior from outside the provider.

### 161. Tor

**Definition:** "The Onion Router" — Tor is a free, decentralized anonymity **network**, designed to make a user's identity and browsing activity very difficult to trace, by routing traffic through multiple independent relay nodes with layered encryption. **Tor Browser** is a separate, specific browser application designed to access the Tor network conveniently and safely — Tor (the network/protocol) and Tor Browser (the application) are related but distinct things.

### 162. Tor Nodes

**Definition:** The relay computers (run by volunteers worldwide) that make up the Tor network. Traffic passes through (typically) three types of nodes:

- **Entry (Guard) Node:** The first node your traffic reaches — it knows your real IP address, but not your final destination.
- **Middle Node(s):** Relay(s) that pass encrypted traffic along — knows neither your identity nor the final destination in full.
- **Exit Node:** The last node before traffic reaches its destination — it knows the destination, but not your original identity.

**Important points:** No single relay normally has knowledge of both the user's original IP address and the final destination — No single relay normally sees both the user's original IP address and the final destination. However, an adversary capable of observing traffic at both ends may perform traffic-correlation attacks. Tor normally uses three relays; adding more hops is not generally considered a security improvement and increases latency.

### 163. Onion Routing

**Definition:** The layered encryption technique behind Tor's name — your data is wrapped in multiple layers of encryption (like an onion), one layer per relay node in the path. Each node peels off (decrypts) only its own outer layer, revealing just enough information to know the next hop, without seeing the full path or original content.

### 164. Dark Web

**Definition:** The dark web refers to services intentionally hosted or accessed through overlay networks, and not directly reachable through the ordinary public web via standard browsers/search engines; Tor `.onion` services are a common example, though other overlay networks exist too.

**Important points:** The Tor network runs noticeably slower than regular browsing, largely because traffic is deliberately routed through multiple encrypted relay hops around the world instead of taking a direct path.

### 165. `.onion`

**Definition:** `.onion` is a special-use domain suffix associated with Tor onion services — reachable only through the Tor network, not through regular DNS/browsers. It is not a top-level domain in the ordinary sense (it is not part of the standard public DNS root); it is a reserved special-use suffix recognized by Tor-aware software.

## Part 16 — HTTP In Depth

*(This section builds on the basic HTTP/HTTPS definitions in 142/143, with the level of detail needed for Web Development and technical interviews: the anatomy of a request/response, methods, headers, and status codes.)*

### 166. HTTP Request & Response Cycle

**Definition:** HTTP is a **request-response protocol** — a client (usually a browser) sends a request to a server, and the server processes it and sends back a response. Each request-response pair is (by default) independent; HTTP itself does not remember previous requests (it is "stateless" — see Cookies/Sessions, 173/174, for how applications add state on top).

**How it works, step by step:**

```
Browser (Client)                          Server
      |----------- HTTP Request -------------->|
      |                                         | (server processes the request:
      |                                         |  reads the URL, method, headers,
      |                                         |  body; looks up data; runs logic)
      |<---------- HTTP Response --------------|
```

**Related concepts:** TCP (119) carries the request/response as the underlying transport; TLS (153) encrypts it for HTTPS (143).

### 167. HTTP Request Structure

**Definition:** In **HTTP/1.x** (1.0 and 1.1), every HTTP request is written as text with three parts: a **request line**, a set of **headers**, and an optional **body**. (HTTP/2 and HTTP/3 carry this same conceptual information — method, path, headers, body — but encode it using binary framing rather than this literal text format; see the note at the end of Part 16.)

**Example — a raw HTTP/1.1 request:**

```
POST /api/users HTTP/1.1              <- Request line: Method + Path + Version
Host: example.com                     <- Headers
Content-Type: application/json
Authorization: Bearer eyJhbGciOi...
Content-Length: 27

{"name": "Asha", "age": 25}           <- Body (the actual data being sent)
```

**Parts explained:**

- **Request line:** the HTTP method (169), the requested path/resource, and the HTTP version.
- **Request headers:** metadata about the request (e.g., which host, what data format is being sent, authentication credentials). See 170 for common headers.
- **Request body:** the actual payload being sent — present for methods like POST/PUT/PATCH; typically absent for GET.

### 168. HTTP Response Structure

**Definition:** In **HTTP/1.x**, every HTTP response is written as text with three parts: a **status line**, a set of **headers**, and an optional **body**. (As with the request structure above, HTTP/2 and HTTP/3 represent the same information — status code, headers, body — using binary framing rather than this literal text format.)

**Example — a raw HTTP/1.1 response:**

```
HTTP/1.1 201 Created                          <- Status line: Version + Status Code + Reason
Content-Type: application/json                <- Headers
Content-Length: 58

{"id": 42, "name": "Asha", "age": 25}          <- Body (the actual data returned)
```

**Parts explained:**

- **Status line:** the HTTP version, the numeric status code, and a short human-readable reason phrase. See 171 for the full status code reference.
- **Response headers:** metadata about the response (e.g., content type, caching rules, where a cookie should be stored). See 170.
- **Response body:** the actual data returned — HTML for a webpage, JSON for an API, or empty for some responses (e.g., a 204 No Content).

### 169. HTTP Methods

**Definition:** The method (also called "verb") in the request line tells the server what action the client wants to perform on the given resource.

| Method | Purpose | Typically has a body? | Idempotent? | Safe (read-only)? |
|---|---|---|---|---|
| **GET** | Retrieve data | No | Yes | Yes |
| **POST** | Submit/process data; commonly used to create resources | Yes | No | No |
| **PUT** | Replace a resource entirely | Yes | Yes | No |
| **PATCH** | Partially modify a resource | Yes | Not inherently — depends on how the specific operation/API is designed | No |
| **DELETE** | Remove a resource | No (usually) | Yes | No |
| HEAD | Like GET, but returns only headers, no body | No | Yes | Yes |
| OPTIONS | Asks what methods/headers are allowed on a resource | No | Yes | Yes |

**What "idempotent" means:** calling the method multiple times has the same effect as calling it once (e.g., `DELETE /users/5` twice still just results in user 5 being deleted — the second call doesn't do anything further). POST is **not** idempotent — submitting the same POST twice typically creates two resources.

**Example (web development context):** A typical REST API for a blog:

```
GET    /posts       -> list all posts
GET    /posts/12     -> get post #12
POST   /posts        -> create a new post (body has the content)
PUT    /posts/12     -> replace post #12 entirely
PATCH  /posts/12     -> update only some fields of post #12
DELETE /posts/12     -> delete post #12
```

**Related concepts:** OPTIONS is also used as the "preflight" method in CORS — see 178.

### 170. HTTP Headers

**Definition:** Key-value pairs sent in both requests and responses, carrying metadata that isn't part of the actual body content.

**Common Request Headers:**

| Header | Purpose |
|---|---|
| `Host` | Which domain the request is for (needed since one server/IP can host multiple sites) |
| `Content-Type` | Format of the request body (e.g., `application/json`, `multipart/form-data`) |
| `Authorization` | Credentials (e.g., `Bearer <token>`) for authenticating the request |
| `Cookie` | Cookies previously stored by the browser for this domain (see 173) |
| `Accept` | What response formats the client can understand (e.g., `application/json`) |
| `User-Agent` | Identifies the client software (browser/app) making the request |

**Common Response Headers:**

| Header | Purpose |
|---|---|
| `Content-Type` | Format of the response body |
| `Content-Length` | Size of the response body in bytes |
| `Set-Cookie` | Instructs the browser to store a cookie (see 173) |
| `Cache-Control` | Caching rules for the response (see 176) |
| `Location` | Where to redirect to (used with 3xx status codes) |
| `Access-Control-Allow-Origin` | Which origins are allowed to read this response (see 178, CORS) |

### 171. HTTP Status Codes

**Definition:** A 3-digit numeric code in the response's status line, indicating the outcome of the request. The first digit defines the general category.

| Range | Category | Meaning |
|---|---|---|
| **1xx** | Informational | Request received, processing continues (rarely seen directly in app development) |
| **2xx** | Success | The request was successfully received, understood, and accepted |
| **3xx** | Redirection | Further action is needed to complete the request — usually a redirect to a different URL, though not always (e.g., 304 signals a valid cache rather than a new location) |
| **4xx** | Client Error | The request has a problem (bad syntax, unauthorized, not found) |
| **5xx** | Server Error | The server failed to fulfill a valid request |

**Common status codes you'll actually encounter:**

| Code | Meaning | Typical situation |
|---|---|---|
| **200** OK | Success | Standard successful GET/PUT/PATCH response |
| **201** Created | Success | A POST successfully created a new resource |
| **301** Moved Permanently | Redirect | Resource permanently moved to a new URL |
| **302** Found | Redirect | Resource temporarily at a different URL |
| **304** Not Modified | Caching (3xx, but not a redirect) | Indicates the cached representation has not changed and the client can use its cached copy — see 176 |
| **400** Bad Request | Client error | Malformed request (e.g., invalid JSON) |
| **401** Unauthorized | Client error | Missing/invalid authentication credentials |
| **403** Forbidden | Client error | Request understood, but the server refuses to authorize it |
| **404** Not Found | Client error | Resource doesn't exist at this URL |
| **500** Internal Server Error | Server error | Generic server-side failure (e.g., unhandled exception) |
| **502** Bad Gateway | Server error | A server acting as a gateway/proxy (see 180) got an invalid response from the upstream server |
| **503** Service Unavailable | Server error | Server temporarily overloaded or down for maintenance |

**Important points:** 401 vs 403 is a common interview question. **401 Unauthorized** means authentication is required or has failed (the server doesn't know who you are, or your credentials were rejected). **403 Forbidden** means the server understood the request but refuses to authorize it (regardless of the specific reason — which may or may not relate to who the requester is).

### 172. HTTP Persistent Connections (Keep-Alive)

**Definition:** HTTP/1.1 normally uses persistent connections, allowing multiple requests/responses to reuse a single underlying TCP connection (119, 122), instead of opening and closing a brand-new TCP connection for every single request.

**Why it is needed:** Setting up a TCP connection (three-way handshake, 122) — and a TLS handshake (153) for HTTPS — has real overhead. Reusing the same connection for several requests (e.g., loading an HTML page plus its CSS, JS, and image files) avoids repeating that overhead every time, significantly speeding up page loads.

**How it works:** In HTTP/1.1, connections are persistent **by default** — no special header is required to enable this behavior. The `Connection` header is used for connection-*management* rather than for turning persistence on: a client or server can send `Connection: close` to explicitly signal that the connection should be closed after the current response, and (mainly in the older HTTP/1.0, where connections were closed by default) `Connection: keep-alive` was used to explicitly request a persistent connection. In modern HTTP/1.1 usage you'll still often see `Connection: keep-alive` sent, but it is reinforcing default behavior rather than switching it on.

#### HTTP/1.1 vs HTTP/2 vs HTTP/3

**HTTP/1.1:** Uses persistent connections (above) — requests and responses are still handled essentially one-at-a-time per connection (a browser typically works around this by opening several parallel connections to the same server).

**HTTP/2:** Introduces **binary framing** (requests/responses are broken into binary frames rather than sent as plain text) and **multiplexing** — multiple requests/responses can be in flight concurrently over a single connection, rather than one at a time. Also adds **header compression** to reduce repeated header overhead across requests.

**HTTP/3:** Built on **QUIC**, a transport protocol that runs over **UDP** instead of TCP. It keeps HTTP/2's multiplexed-streams model, but because QUIC manages reliability itself per-stream, a lost packet affecting one stream doesn't stall the other streams on the same connection — avoiding a limitation (head-of-line blocking at the TCP level) that can still affect HTTP/2 running over TCP.

**Important points:** These are progressively more sophisticated ways of reusing a connection efficiently — HTTP/2 and HTTP/3 are not simply "the same Keep-Alive mechanism as HTTP/1.1"; each changes the underlying connection model. Knowing that they exist and their core distinguishing idea (multiplexing; QUIC/UDP for HTTP/3) is generally sufficient for Web Development and interview purposes.

## Part 17 — Browser & Web Security

*(These topics explain how modern web applications maintain state and enforce security across the stateless HTTP protocol (166) — essential for Web Development.)*

### 173. Cookies

**Definition:** A small piece of data that a server asks the browser to store (via the `Set-Cookie` response header, 170), which the browser automatically sends the cookie on requests that match the cookie's domain, path, security, and other applicable rules.

**Why it is needed:** HTTP itself is stateless (166) — the server has no built-in memory of previous requests from the same client. Cookies give web applications a way to persist small bits of information (like "this browser is logged in as user #42") across multiple requests.

**How it works, step by step:**

```
1. Browser sends a request (e.g., logs in with username/password).
2. Server validates the login and responds with:
     Set-Cookie: session_id=abc123; HttpOnly; Secure; Max-Age=3600
3. Browser stores this cookie for the server's domain.
4. On every later request to that same domain, the browser automatically
   attaches:  Cookie: session_id=abc123
5. Server reads the cookie to identify "this request is from user #42."
```

**Important points:** Common cookie attributes: `HttpOnly` (JavaScript on the page cannot read this cookie, reducing certain attack risks), `Secure` (only sent over HTTPS), `Max-Age`/`Expires` (how long the cookie persists), `SameSite` (restricts whether the cookie is sent on cross-site requests).

### 174. Sessions

**Definition:** A session is a mechanism for maintaining state across multiple HTTP requests, commonly using a session identifier stored in a cookie — since HTTP itself is stateless (166), a session is how a server recognizes that a sequence of separate requests belong to the same ongoing user interaction (e.g., "logged in as this user").

**How it works:** Instead of storing all user data in the cookie itself, the server generates a random **session ID**, stores the actual session data (who's logged in, cart contents, etc.) on the server side (in memory, a database, or a cache like Redis), and only sends the session ID to the browser as a cookie. On each request, the server looks up the session ID to retrieve that user's data.

**Related concepts:** Session Layer (90) in the OSI model is the conceptual origin of this idea; in practice, on the modern web, sessions are implemented at the application layer using cookies, not by a dedicated OSI Session-layer protocol.

### 175. Session Management

**Definition:** The overall approach an application uses to create, track, and expire user sessions.

**Two common approaches:**

- **Server-side sessions (stateful):** The server stores session data itself (as in 174) and only gives the client an opaque session ID. Easy to invalidate (just delete the server-side record), but requires the server to maintain state — which can complicate scaling across multiple servers unless sessions are shared (e.g., via a common database/cache).
- **Token-based authentication:** The server issues a token (e.g., containing user ID, expiry, and a signature) that the client presents on each request instead of a server-looked-up session ID. Token-based authentication *can* be stateless when the server does not maintain any session state and simply verifies the token's signature on each request — **JWT (JSON Web Token) is one common type of token** used this way, but "token-based" and "stateless" are not automatically the same thing (a server can still track issued tokens server-side, e.g., to support revocation). A purely stateless approach is easier to scale (no shared session storage needed) but harder to forcibly invalidate a single token before it naturally expires.

**Important points:** Both approaches ultimately rely on the browser sending some kind of identifying value (a cookie, or an `Authorization` header, 170) back on every request.

### 176. Browser Caching

**Definition:** The practice of a browser storing a copy of a previously fetched resource (HTML, CSS, JS, images) locally, so it can reuse that copy instead of re-fetching it from the server on a later visit — speeding up page loads and reducing server load.

**How it works, step by step:**

```
1. Browser requests a file (e.g., style.css).
2. Server responds with the file plus caching headers, e.g.:
     Cache-Control: max-age=3600
     ETag: "a1b2c3"
3. Browser stores the file AND the caching rules.
4. On the NEXT request for the same file, within the max-age window,
   the browser uses its local copy directly -- no network request at all.
5. Once the cache expires, the browser sends a "conditional request"
   (If-None-Match: "a1b2c3") asking "has this changed?"
     - If unchanged, server replies with 304 Not Modified (171) and
       an empty body -- browser reuses its cached copy.
     - If changed, server replies with 200 OK and the new file.
```

**Important points:** `Cache-Control` and `ETag` (or `Last-Modified`) are the two main mechanisms — `Cache-Control` avoids the network request entirely for a while, while `ETag`/conditional requests let the browser cheaply verify whether a fresh copy is even needed.

### 177. Same-Origin Policy (SOP)

**Definition:** A fundamental browser security rule stating that a web page can only freely read data from (or make certain kinds of requests to) another URL if that URL has the **same origin** — the browser blocks a page from reading responses from a *different* origin by default, unless that origin explicitly allows it (see CORS, 178).

**What "origin" means:** An origin is the combination of **scheme (protocol) + host (domain) + port**. Two URLs are the **same origin** only if all three match exactly.

**Example:**

```
Page loaded from:  https://example.com

https://example.com/api        -> SAME origin (scheme, host, port all match)
http://example.com/api         -> DIFFERENT origin (scheme differs: http vs https)
https://api.example.com/       -> DIFFERENT origin (host differs: subdomain)
https://example.com:8080/      -> DIFFERENT origin (port differs)
```

**Why browsers enforce it:** Without this rule, a malicious website you visit could silently make requests to, say, your bank's website using your logged-in cookies, and read the response — stealing your data. Same-Origin Policy is the core defense against this class of attack.

### 178. CORS (Cross-Origin Resource Sharing)

**Definition:** A mechanism that lets a server explicitly relax the Same-Origin Policy (177) for specific other origins — allowing a web page hosted on one origin to make requests to, and read responses from, a server on a *different* origin, when that server opts in.

**Why it is needed:** Modern web apps routinely need to call APIs hosted on a different origin (e.g., a frontend on `app.example.com` calling an API on `api.example.com`). Without CORS, the browser's Same-Origin Policy would silently block the frontend JavaScript from reading the API's response.

**How the server allows a cross-origin request:** The server includes specific response headers telling the browser which origins (and methods/headers) are permitted:

```
Access-Control-Allow-Origin: https://app.example.com
Access-Control-Allow-Methods: GET, POST, PUT, DELETE
Access-Control-Allow-Headers: Content-Type, Authorization
```

If the requesting page's origin isn't allowed, the browser blocks the frontend JavaScript from reading the response (the request may still technically reach the server, but the browser won't hand the response back to the page's script).

**Preflight request (conceptual level):** Some cross-origin requests require a browser CORS preflight using **OPTIONS** (169) before the actual request — this typically applies to requests that aren't "simple" (e.g., using methods like PUT/DELETE, or custom headers like `Authorization`). The browser automatically sends the OPTIONS request first, asking "would you allow this actual request?" before sending the real one.

```
Browser: OPTIONS /api/users   (preflight - "can I send a DELETE with this header?")
Server:  200 OK + Access-Control-Allow-* headers  ("yes, here's what's allowed")
Browser: DELETE /api/users/5  (the actual request, now sent)
```

**Important points:** CORS is enforced **by the browser**, not the server — it's a client-side protection. A non-browser client (like a backend server, or a tool such as `curl`) is not restricted by CORS at all; CORS exists specifically to protect *users* browsing with a browser that automatically attaches their cookies/credentials to requests.

## Part 18 — Modern Web Infrastructure

*(These are the infrastructure pieces that sit between a browser and an application's actual business logic in most real-world, production web systems.)*

### 179. CDN (Content Delivery Network)

**Definition:** A geographically distributed network of servers that cache and serve a website's static content (images, CSS, JS, video) from a location physically close to each user, instead of every user fetching it from one original (origin) server.

**Why it is needed:** The further data has to physically travel, the higher the latency (12). A user in India fetching an image from a server in the US will experience more delay than fetching it from a CDN server located in India.

**How it works, step by step:**

```
Without CDN:
User (India) -----------------------------------> Origin Server (USA)
                    (long distance, higher latency)

With CDN:
User (India) ---> Nearest CDN Edge Server (India) ---(occasionally)---> Origin Server (USA)
              (short distance, low latency; edge server has a cached copy
               of the content, so it usually doesn't need to contact
               the origin server at all)
```

**Example:** Loading images/CSS/JS for a website from providers like Cloudflare, Akamai, or a cloud provider's CDN — the browser fetches these files from a nearby edge server rather than the application's main server.

**Related concepts:** DNS (140) is often used to direct users to their nearest CDN edge server automatically.

### 180. Reverse Proxy

**Definition:** A server that sits in front of one or more backend/application servers. The client sends requests to the reverse proxy, which forwards them to one or more backend servers on the client's behalf — in typical deployments, the client interacts only with the reverse proxy and doesn't address backend servers directly.

**Why it is needed:** Centralizes concerns like TLS termination (handling HTTPS encryption/decryption in one place), request routing, compression, and hides the internal server architecture from the outside world (clients don't know or care how many backend servers exist, or their internal addresses).

**How it works:**

```
Browser  --->  Reverse Proxy  --->  Application Server
                (e.g., Nginx)        (e.g., Node.js/Django app)
```

The reverse proxy receives the request, may modify/inspect it (e.g., add headers, terminate TLS), and forwards it to the correct backend server, then relays that server's response back to the client — the client is never aware that a backend server was involved at all.

**Example:** Nginx or a cloud load balancer configured to forward all requests for `example.com` to an internal application server running on a private port.

### 181. Load Balancer

**Definition:** A load balancer distributes incoming traffic across multiple backend servers according to configured algorithms and health status, to spread the load and avoid overwhelming any single server.

**Why it is needed:** A single server has limited capacity. As traffic grows, running multiple identical copies of the application ("horizontal scaling") and distributing requests among them lets the system handle far more load — and provides redundancy if one server fails.

**How it works:**

```
Browser  --->  Load Balancer  --->  Server 1
                                --->  Server 2
                                --->  Server 3
```

The load balancer picks which server should handle each incoming request, using a strategy such as **round robin** (cycle through servers in order), **least connections** (send to whichever server currently has the fewest active requests), or based on server health (skip servers that are down).

**Comparison — Reverse Proxy vs Load Balancer:** A reverse proxy's core job is *fronting/hiding* backend servers (often just one); a load balancer's core job is *distributing* traffic across *multiple* servers. In practice, the same piece of software (e.g., Nginx, HAProxy, a cloud load balancer) very often does both jobs at once.

### 182. WebSocket

**Definition:** WebSocket provides a **persistent, full-duplex** connection between a browser and a server that allows both client and server to send messages at any time — unlike regular HTTP, where the client must always initiate each request.

**Why it is needed:** Regular HTTP is request-response only (166) — the server cannot push data to the client unless the client asks for it first. Real-time features (live chat, live notifications, collaborative editing, live price updates) need the server to be able to push data to the client immediately, as soon as something happens.

**How it works, step by step:**

```
1. Browser sends a normal HTTP request asking to "upgrade" the connection:
     GET /chat HTTP/1.1
     Upgrade: websocket
     Connection: Upgrade

2. Server agrees and responds:
     HTTP/1.1 101 Switching Protocols

3. The underlying TCP connection (119) is now a WebSocket connection --
   both browser and server can send messages to each other at any time,
   without needing a new request/response cycle for each message.
```

**Comparison — HTTP vs WebSocket:**

| Aspect | HTTP | WebSocket |
|---|---|---|
| Direction | Client requests, server responds | Either side can send anytime (full-duplex) |
| Connection | Often short-lived per request (though reused via Keep-Alive, 172) | Long-lived, stays open |
| Use case | Regular web pages, REST APIs | Live chat, live notifications, real-time games/dashboards |

**Important points:** A WebSocket connection starts as a normal HTTP request (the "upgrade handshake") and then switches protocols — this is why WebSocket servers are often set up behind the same reverse proxy/load balancer (180/181) as the rest of an application.

## Part 19 — Practical Understanding: End-to-End Examples

These walkthroughs connect multiple concepts from earlier sections together, referenced by topic number, rather than re-explaining anything from scratch.

### Example 1 — What happens when I type `https://google.com` into a browser?

```
1. DNS Resolution (140/Part 13): Browser looks up "google.com" -> gets IP address.

2. TCP Connection (122): Browser opens a TCP connection to that IP on port 443,
   using the Three-Way Handshake (SYN, SYN-ACK, ACK).

3. TLS Handshake (153): Browser and server negotiate encryption; server
   proves identity via certificate; a secure encrypted channel is established.

4. HTTPS Request (143): Browser sends an encrypted HTTP request for the page.

5. Packets travel: Application data -> Segment -> Packet -> Frame -> bits
   (Encapsulation, 18), routed hop-by-hop through your Router (41),
   your ISP's network, and backbone routers (Routing, Part 14), each
   decrementing TTL (112), until reaching Google's server.

6. Server processes the request and sends back an encrypted HTTPS response,
   which is Decapsulated (19) at your device, layer by layer.

7. Browser renders the received HTML/CSS/JS as the web page you see.
```

### Example 2 — How two devices communicate inside a LAN

```
Device A (192.168.1.10) wants to send data to Device B (192.168.1.20),
both on the same LAN.

1. Device A checks: is B on the same subnet? Yes (same Network ID, 59).
2. Device A needs B's MAC address -> sends an ARP Request (79, broadcast).
3. Device B replies with an ARP Reply (80) containing its MAC address.
4. Device A builds a Frame (17) with B's MAC as destination and sends it.
5. If connected via a Switch (38), the switch forwards the frame only to
   B's port, using its MAC Address Table (77) -- no IP routing needed
   at all for this local, same-subnet delivery.
```

### Example 3 — How a packet travels from my laptop to a remote server

See the complete step-by-step diagram already given in **Part 14 — Routing**, under "Full Example: A Packet's Journey Through Multiple Routers."

### Example 4 — How NAT works

See the complete worked example already given in **69. NAT**.

### Example 5 — How ARP finds a MAC address

See the complete worked example already given in **80. ARP Reply**.

### Example 6 — How subnetting divides a network

See the complete worked example already given in **68. Subnetting**.

### Example 7 — How TCP establishes a connection

See the complete worked example already given in **122. TCP Three-Way Handshake**.

### Example 8 — How VPN changes the path/visibility of traffic

```
WITHOUT VPN:
Your Device ---> ISP (sees destination + can DPI unencrypted traffic) ---> Website
   (Website sees YOUR real public IP address)

WITH VPN:
Your Device --[Encrypted Tunnel, 155]--> VPN Server --> Website
   (ISP only sees you're connected to the VPN server, nothing else)
   (Website sees the VPN SERVER's IP address, not yours)
```

This single diagram ties together: Encryption (150), VPN Tunnel (155), ISP Visibility (157), and Public/Private IP Address (49/50) — each of which has its own full section if you need to revisit the underlying concept.

### Example 9 — The Full Web Development Request Flow

This is the single most useful mental model for Web Development: the complete journey from a user typing a URL to seeing a rendered, interactive page. Every step just links back to its full explanation elsewhere in these notes — nothing is re-explained here.

```
User enters a website URL
   |
   v
DNS Resolution (140, Part 13) -- domain name is translated to an IP address
   |
   v
Network Routing (Part 14) -- packets find their way to the server's network
   |
   v
TCP Connection (119, 122) -- three-way handshake establishes a reliable connection
   |
   v
TLS Handshake (153) -- only for HTTPS (143); encrypts the connection
   |
   v
HTTP Request (166, 167) -- browser sends a request with a Method (169) and Headers (170)
   |
   v
Reverse Proxy / Load Balancer (180, 181) -- (if present) receives the request first,
   |                                          and routes it to an available backend
   v
Application Server -- runs the actual business logic, queries a database, etc.
   |
   v
HTTP Response (166, 168) -- Status Code (171), Headers (170), and a Body are sent back
   |
   v
Browser
   |
   +--> Cookies (173) may be stored from Set-Cookie headers
   |
   +--> Browser Caching (176) rules are noted for next time
   |
   +--> Browser renders the HTML/CSS/JS into the page the user sees
```

**Important points:** A CDN (179) may serve static assets (images, CSS, JS) directly from a nearby edge location, bypassing several of the later steps entirely for those specific files. If the page opens a WebSocket (182) after loading (e.g., for live chat), that connection stays open separately from this request/response flow, allowing the server to push further updates at any time.
