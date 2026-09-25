# Computer Networks — Short Notes (Quick Revision)

Same numbering as `Computer_Networks_Complete.pdf` and `README_Complete.md`. **Every numbered topic in the PDF has its own entry below — no numbers are skipped.** For full explanations, examples and diagrams, open the complete PDF at the matching number.

---

## Part 1 — Fundamentals

**1. Computer Network:** Devices connected to exchange data/share resources, using shared protocols.
**2. Network Components:** End devices, intermediate devices (hub/switch/router), transmission media, protocols.
**3. Client-Server:** Dedicated servers provide services; clients request them. Centralized, easy to secure.
**4. Peer-to-Peer:** Every device is both client and server. Decentralized — can reduce dependence on a single central server.
**5. Internet:** Global "network of networks," primarily using the Internet protocol suite.
**6. ARPANET:** One of the first major operational packet-switching networks (1969); an important ancestor of the Internet.
**7. Analog Signal:** Continuous, smoothly varying signal.
**8. Digital Signal:** Discrete signal (e.g., 0/1); digital systems can often regenerate signals, improving noise tolerance.
**9. Modem:** Modulator-Demodulator — adapts/modulates signals for transmission over a particular access medium; traditional telephone modems converted digital data to/from analog signals.
**10. Data Communication:** Needs delivery, accuracy, timeliness, low jitter.
**11. Bandwidth:** Max data-transfer capacity of a link (bps).
**12. Latency:** Delay before data starts arriving (e.g., ping time).
**13. Throughput:** Actual real-world data transferred (vs bandwidth's theoretical max).
**14. Packet:** Formatted data unit (general term, mainly Network layer).
**15. Segment:** Transport-layer (TCP) data unit.
**16. Datagram:** A connectionless data unit; an IP datagram belongs to the Network layer, while a UDP datagram belongs to the Transport layer.
**17. Frame:** Data Link-layer data unit (has MAC header + trailer).
**18. Encapsulation:** Adding headers layer by layer going down (App→Physical).
**19. Decapsulation:** Stripping headers layer by layer going up (Physical→App).

## Part 2 — Switching

**20. Circuit Switching:** Dedicated path reserved for whole session (e.g., old telephony). Wasteful when idle.
**21. Message Switching:** Whole message stored & forwarded hop by hop. Historical.
**22. Packet Switching:** Data split into independently-routed packets. **Used by the modern Internet.**
**23. Comparison of Switching Techniques:** Packet switching shares network links dynamically and can reroute traffic when paths fail; it is the switching method used by the modern Internet.
**24. Transmission Media:** Guided (wired) vs unguided (wireless) paths for signals.
**25. Wired Communication:** Twisted pair, coaxial, fibre-optic (very high bandwidth, commonly used for backbones).
**26. Wireless Communication:** Wi-Fi, Bluetooth, cellular, satellite.

## Part 3 — Types of Networks

**27. LAN:** Small area (home/office), high speed, low latency.
**28. MAN:** City-wide, connects multiple LANs.
**29. WAN:** Country/global, connects multiple MANs/LANs. Internet = largest WAN.
**30. PAN:** Very short range (e.g., Bluetooth earbuds).
**31. Network Topologies:** The layout pattern of devices/connections; affects cost, fault tolerance, scalability.
**32. Bus Topology:** Single shared cable. Cheap, but one break = whole network down.
**33. Star Topology:** All devices → central switch/hub. Most common today; hub failure = outage.
**34. Ring Topology:** Devices in a loop, data hops around. Legacy (Token Ring).
**35. Mesh Topology:** Full mesh connects every device to every other device; partial mesh connects selected devices. Provides redundancy but can be expensive/complex.
**36. Hybrid Topology:** Combination of two+ topologies (e.g., star-bus).

## Part 4 — Network Devices

**37. Hub:** L1, repeats incoming signals to the other connected ports. Obsolete.
**38. Switch:** L2, forwards by MAC address using a MAC table. Efficient.
**39. Bridge:** L2, connects/filters between 2 segments. Switch = multi-port bridge.
**40. Repeater:** L1, receives a signal and regenerates/retransmits it.
**41. Router:** L3, forwards packets between *different* networks using IP addresses and a routing table; many home/office routers also perform NAT.
**42. Gateway:** Connects a network to another network; may translate between protocols in some contexts. Default gateway = router used to reach other networks.
**43. NIC:** Associated with a MAC address — physical interfaces often factory-assigned, virtual/software interfaces may use software-assigned addresses; one MAC per NIC.
**44. Modem:** See (9) — adapts/modulates signals for the ISP access medium; traditional telephone modems converted digital data to/from analog signals.
**45. Access Point:** Bridges wireless devices to a wired LAN.

## Part 5 — IP Addressing

**46. IP Address:** Numeric address assigned to a network interface, identifying its location on a network for routing.
**47. IPv4:** 32-bit, dotted decimal (e.g., `192.168.1.10`). ~4.3B addresses.
**48. IPv6:** 128-bit, hex colon notation. Solves IPv4 exhaustion.
**49. Public IP:** Globally unique, routable on Internet.
**50. Private IP:** Reserved for use within private/internal networks and not routable on the public Internet. Ranges: `10.0.0.0/8`, `172.16.0.0/12`, `192.168.0.0/16`.
**51. Static IP:** Manually fixed, doesn't change.
**52. Dynamic IP:** Automatically assigned by a network configuration mechanism such as DHCP (for IPv4), and can change.
**53. IPv4 Address Classes:** Historical (pre-CIDR) system — modern networking uses CIDR instead.
**54. Class A:** `1–126`. Huge networks (16M+ hosts each).
**55. Class B:** `128–191`. Medium networks (~65,000 hosts each).
**56. Class C:** `192–223`. Small networks (254 hosts each) — most home/office ranges.
**57. Class D:** `224–239`. Used for multicast communication.
**58. Class E:** `240–255`. Reserved/experimental, unused.
**59. Network ID:** Shared network portion of an IP (from subnet mask).
**60. Host ID:** Unique per-device portion of an IP.
**61. Network Address:** Host bits all 0 → identifies the network (not assignable).
**62. Broadcast Address:** Host bits all 1 → sends to everyone on subnet.
**63. Loopback Address:** `127.0.0.1` — device talking to itself (localhost).
**64. IANA:** Coordinates global IP address allocation, DNS root-zone management, and protocol parameters → RIRs → ISPs.
**65. ISP and IP Allocation:** ISPs buy blocks from RIRs, assign to customers.
**66. Subnet Mask:** Marks network vs host bits (e.g., `255.255.255.0` = `/24`).
**67. CIDR:** Modern classless addressing, `IP/prefix`, flexible sizing.
**68. Subnetting:** Splitting a network into smaller subnets by borrowing host bits.
> Example: `192.168.1.0/24` → four `/26` subnets of 64 addresses each (62 usable).
**69. NAT:** Translates IP addresses between private/internal and public/external addressing.
**70. PAT:** A form of NAT — port numbers let *many* private IPs share *one* public IP simultaneously.

## Part 6 — MAC Address / LAN Communication

**71. MAC Address:** 48-bit Layer 2/link-layer address associated with a network interface. Physical NICs often have a factory-assigned address; virtual interfaces/OS can use software-assigned addresses. Can be overridden ("spoofed"/randomized) — not permanently fixed.
**72. MAC Address Structure:** `OUI (24 bits) : device/interface-specific identifier (24 bits)`, hex, e.g. `00:1A:2B:3C:4D:5E` (universally administered example).
**73. OUI:** For a universally administered MAC address, the first 24 bits identify the organization under an IEEE-assigned OUI.
**74. NIC and MAC Addresses:** One MAC per NIC; multiple NICs = multiple MACs.
**75. MAC vs IP:** MAC = Layer 2/link-layer address associated with a network interface, LAN-local. IP = logical address; may be private/local or globally routable depending on the address.
**76. Ethernet:** Dominant wired LAN framing standard.
**77. MAC Address Table:** Switch's map of MAC → port.
**78. ARP:** Resolves an IPv4 address to a MAC address within a local network.
**79. ARP Request:** Broadcast — "who has this IP?"
**80. ARP Reply:** Unicast — "I do, here's my MAC."
**81. ARP Cache:** Stores recent IP→MAC mappings temporarily.
**82. Unicast:** One → one.
**83. Broadcast:** One → all.
**84. Multicast:** One → interested group.

## Part 7 — OSI Model

**85. OSI Model:** Theoretical 7-layer reference model (ISO).

| # | Layer | Data unit | Addressing | Example protocol |
|---|---|---|---|---|
| 7 | Application | Data | — | HTTP, DNS |
| 6 | Presentation | Data | — | Encryption/compression |
| 5 | Session | Data | — | Session/login mgmt |
| 4 | Transport | Segment | Port | TCP, UDP |
| 3 | Network | Packet | IP | IP, ICMP |
| 2 | Data Link | Frame | MAC | Ethernet |
| 1 | Physical | Bit | — | Cables, radio |

**86. Physical Layer:** Layer 1 — raw bits over cable/radio/light. No addressing.
**87. Data Link Layer:** Layer 2 — frames, MAC addressing, hop-to-hop delivery, error detection.
**88. Network Layer:** Layer 3 — packets, IP addressing, routing.
**89. Transport Layer:** Layer 4 — segments, port numbers, TCP/UDP.
**90. Session Layer:** Layer 5 — session establishment, synchronization, and checkpoints in the OSI reference model. Authentication/authorization and session hijacking are security/application concepts rather than core Session-layer functions (cookies/tokens are application-level mechanisms, covered in Part 17).
**91. Presentation Layer:** Layer 6 — data translation, encryption, compression.
**92. Application Layer:** Layer 7 — end-user network protocols (HTTP, DNS, etc.).
> A traditional IP router primarily operates at Layers 1–3 for packet forwarding.

## Part 8 — Data Link Layer Deep Dive

**93. Framing:** Marks frame boundaries; adds MAC header + trailer.
**94. MAC Addressing:** A data-link frame carries source/destination MAC addresses around the packet (full detail at 71).
**95. Error Detection:** CRC/checksum can detect corruption — they don't correct it.
**96. Error Correction:** Fixes error without retransmission (adds redundancy).
**97. Flow Control (DLL):** Prevents overwhelming receiver at link level (per-hop).
**98. Access Control:** Rules for how devices sharing a medium take turns transmitting.
**99. Collision:** Two devices transmit at the same time on a shared medium, signals interfere.
**100. CSMA/CD:** Historical/shared-medium Ethernet mechanism — detects collisions, backs off, retries. Modern switched full-duplex Ethernet normally has no collisions.
**101. CSMA/CA:** Wi-Fi mechanism that reduces collision probability before transmitting.
**Flow control ≠ Congestion control:** Flow = protect receiver; Congestion = protect network.

## Part 9 — Network Layer Deep Dive

**102. Network Layer:** Core definition at (88) — this Part covers its supporting mechanics.
**103. Logical Addressing:** Addressing by network position (IP), not fixed hardware identity.
**104. Routing:** Selecting paths across networks; packet forwarding is the separate operation of sending packets to the appropriate next hop/interface → full detail in Part 14.
**105. Routing Table:** Router's map of destination → next hop.
**106. Next Hop:** Immediate next router on the path.
**107. Default Gateway:** Router used when destination isn't local.
**108. Packet Forwarding:** Router's core job — check dest IP, look up table, send out correct interface.
**109. Fragmentation:** Splitting a large packet into smaller pieces to fit a smaller MTU; in IPv4 routers may fragment, while in IPv6 routers do not fragment and the source performs fragmentation.
**110. Reassembly:** Rebuilding fragments into the original packet at the destination.
**111. ICMP:** Diagnostics (`ping`). `tracert` on Windows uses ICMP; `traceroute` implementations may use UDP, ICMP, or TCP probes.
**112. TTL:** Hop-count limiter; prevents infinite loops.
**113. Unicast/Multicast/Broadcast Routing:** Same concepts as (82/83/84), applied at the routing/forwarding level.

## Part 10 — Transport Layer

**114. Transport Layer:** Core definition at (89) — this Part is the full deep dive.
**115. Port Numbers:** 16-bit (0–65535); identifies an app/process on a device.
**116. Well-Known Ports (0–1023):** Reserved standard services (80 HTTP, 443 HTTPS, 22 SSH, 53 DNS).
**117. Registered Ports (1024–49151):** Assigned by IANA to specific non-core applications.
**118. Dynamic/Private Ports (49152–65535):** Temporary client-side source ports.
**119. TCP:** Connection-oriented; reliable, ordered delivery via ACKs, sequence numbers, retransmission.
**120. UDP:** Connectionless, low overhead; no retransmission/ordering guarantees, but has a checksum for corruption detection.

**121. TCP vs UDP:**
| | TCP | UDP |
|---|---|---|
| Connection | Yes (handshake) | No |
| Reliable/ordered | Yes (ACKs, seq. numbers, retransmission) | No built-in guarantee |
| Overhead | Higher | Lower |
| Use case | Web, email, files | Streaming, gaming, DNS, VoIP |
> Actual performance depends on network conditions and the app, not just the protocol.

**122. Three-Way Handshake:** `SYN → SYN-ACK → ACK` — synchronizes initial sequence numbers, confirms both sides ready for bidirectional communication.
**123. TCP Connection Termination:** `FIN → ACK → FIN → ACK`
**124. Reliability:** TCP's reliable, ordered delivery under normal conditions (via 125+126+127) — not an absolute guarantee under every failure.
**125. Sequence Numbers:** Number per byte, lets receiver reorder/detect missing data.
**126. Acknowledgements (ACK):** Receiver confirms data received.
**127. Retransmission:** Resend data if no ACK arrives in time.
**128. Flow Control (Transport):** Sliding window — protects receiver.
**129. Congestion Control:** Slow start + backoff — protects network.
**130. Error Control:** Checksum + retransmission.

## Part 11 — TCP/IP Model

**131. TCP/IP Model:** Practical 4-layer model commonly used to describe the Internet protocol suite.

```
OSI 7,6,5 -> TCP/IP Application
OSI 4     -> TCP/IP Transport
OSI 3     -> TCP/IP Internet/Network
OSI 2,1   -> TCP/IP Network Access
```

**132. Application Layer (TCP/IP):** Combines OSI Application+Presentation+Session.
**133. Transport Layer (TCP/IP):** Same as OSI Transport (89) — TCP/UDP, ports.
**134. Internet/Network Layer (TCP/IP):** Same as OSI Network (88) — IP, routing.
**135. Network Access Layer (TCP/IP):** Combines OSI Data Link + Physical.
**136. OSI vs TCP/IP:** OSI = theoretical/7 layers; TCP/IP = practical/4 layers, actually implemented.
**137. OSI-to-TCP/IP Layer Mapping:** See diagram above (131) — 7/6/5→4, 4→3, 3→2, 2/1→1.
**138. Encapsulation in TCP/IP:** Same idea as (18), mapped onto the 4 layers.
**139. Decapsulation in TCP/IP:** Reverse of (138), same idea as (19).

## Part 12 — Protocols Quick Table

| Protocol | Port | Transport | Purpose |
|---|---|---|---|
| DNS (140) | 53 | UDP/TCP | Name → IP |
| DHCP (141) | 67/68 | UDP | Auto IP config |
| HTTP (142) | 80 | TCP (HTTP/1.1, HTTP/2) | Web (unencrypted) |
| HTTPS (143) | 443 | TCP or QUIC/UDP (HTTP/3) | Web (encrypted) |
| FTP (144) | 20/21 | TCP | File transfer |
| SMTP (145) | 25/587 | TCP | Send email |
| SSH (146) | 22 | TCP | Secure remote access |
| ICMP (147) | — | — | Diagnostics |

**140. DNS:** Translates domain names → IP addresses → full detail in Part 13.
**141. DHCP:** Auto-assigns IP config via Discover→Offer→Request→Ack (DORA).
**142. HTTP:** Web protocol; HTTP/1.1 and HTTP/2 commonly use TCP, while HTTP/3 uses QUIC/UDP → full detail in Part 16.
**143. HTTPS:** HTTP + TLS encryption; commonly TCP for HTTP/1.1/2, while HTTP/3 uses QUIC/UDP (443).
**144. FTP:** File transfer, ports 20/21, usually unencrypted.
**145. SMTP:** Sends email (port 25/587).
**146. SSH:** Secure encrypted remote shell access (port 22).
**147. ICMP:** See (111) — diagnostics, not app data.
**148. TCP:** See (119) for full definition.
**149. UDP:** See (120) for full definition.

## Part 13 — DNS

**Flow:** Browser/OS cache → Resolver → Root server → TLD server → Authoritative server → IP returned → cached (per TTL).
**Records:** A (IPv4), AAAA (IPv6), CNAME (alias), MX (mail server), NS (name server).
**13 named root-server identities** are implemented through many geographically distributed anycast instances.

## Part 14 — Routing

**Static routing:** Manual, doesn't adapt, low overhead. Good for small networks.
**Dynamic routing:** Routers auto-share route info via routing protocols, adapts to failures. Good for large networks.
**Every router hop:** check dest IP → routing table lookup → decrement TTL → forward.

## Part 15 — Security & Privacy

**150. Encryption:** Scrambles plaintext into unreadable ciphertext using a key.
**151. Decryption:** Reverses encryption back to plaintext using the correct key.
**152. HTTP vs HTTPS:** HTTPS = TLS-encrypted; ISP generally can't read the content, but may still observe/infer metadata like destination IP and (depending on config) domain. Incognito mode hides nothing from the ISP — only stops local history saving.
**153. TLS:** Cryptographic protocol behind HTTPS.
**154. VPN:** Encrypts + tunnels the traffic routed through a VPN server. Doesn't change your device's own IP — destinations instead see the VPN server's public IP as the traffic source for traffic routed through the VPN.
**155. VPN Tunnel:** The encrypted path between your device and the VPN server; exactly which traffic is routed through it depends on the VPN's configuration.
**156. VPN Server:** The remote server that terminates/decrypts the VPN tunnel traffic and forwards it to the destination; HTTPS content normally remains encrypted end-to-end.
**157. ISP Visibility:** Without VPN — ISP sees destinations. With VPN — ISP generally can't read the encrypted traffic/content, but may observe metadata (VPN server address, timing, volume); the VPN provider can potentially observe/inspect traffic depending on its logging practices.
**158. DPI:** Examines packet headers and, where possible, payload/content to identify, classify, block, or throttle traffic; encryption limits payload inspection.
**159. Proxy vs VPN:** Proxy = typically app-level, may not encrypt. VPN = encrypted tunnel, typically whole-device (depends on config).
**160. VPN Logging:** "No-log" = a trust/policy claim, not independently provable.
**161. Tor:** Anonymity *network* routing traffic through relay nodes. Tor *Browser* is the separate application used to access it.
**162. Tor Nodes:** Entry node (knows your source IP) → Middle node (relays traffic) → Exit node (knows the destination) — no single relay normally sees both. Tor normally uses three relays; adding more hops is not generally a security improvement, and an adversary observing both ends may perform traffic-correlation attacks.
**163. Onion Routing:** Layered encryption, one layer peeled per hop.
**164. Dark Web:** Services intentionally hosted/accessed via overlay networks, not reachable through the ordinary public web; Tor `.onion` is a common example.
**165. `.onion`:** Special-use domain suffix for Tor onion services — not a standard top-level domain.

## Part 16 — HTTP In Depth

**166. HTTP Request & Response Cycle:** Client sends request, server sends response. HTTP is stateless.
**167. HTTP Request Structure:** HTTP/1.x uses a request line (Method + Path + Version) + Headers + optional Body; HTTP/2/3 carry the same information using binary framing.
**168. HTTP Response Structure:** HTTP/1.x uses a status line (Version + Code + Reason) + Headers + optional Body; HTTP/2/3 carry the same information using binary framing.
**169. HTTP Methods:** GET (retrieve), POST (submit/process — commonly creates), PUT (replace), PATCH (partial update), DELETE (remove). GET/PUT/DELETE are idempotent; POST is not.
**170. HTTP Headers:** Metadata key-value pairs. Request: `Host`, `Content-Type`, `Authorization`, `Cookie`. Response: `Content-Type`, `Set-Cookie`, `Cache-Control`, `Location`.
**171. HTTP Status Codes:** 1xx info · 2xx success (200 OK, 201 Created) · 3xx redirect (301, 302, 304) · 4xx client error (400, 401, 403, 404) · 5xx server error (500, 502, 503). **401 = authentication required/failed; 403 = request understood but not authorized.**
**172. HTTP Persistent Connections (Keep-Alive):** HTTP/1.1 normally reuses one TCP connection for multiple requests instead of reconnecting each time. HTTP/2 adds multiplexing (concurrent streams) + header compression over one connection. HTTP/3 runs over QUIC/UDP, keeping multiplexing while avoiding TCP-level head-of-line blocking.

## Part 17 — Browser & Web Security

**173. Cookies:** Small data stored by the browser via `Set-Cookie`, sent back automatically on later requests via `Cookie`. Key flags: `HttpOnly`, `Secure`, `SameSite`.
**174. Sessions:** Mechanism for maintaining state across multiple HTTP requests, commonly via a session ID stored in a cookie.
**175. Session Management:** Server-side sessions (stateful, easy to revoke) vs token-based auth (can be stateless; JWT is one common token type — token-based ≠ automatically stateless).
**176. Browser Caching:** Browser reuses locally stored files using `Cache-Control`/`ETag`; conditional requests get a `304 Not Modified` if unchanged.
**177. Same-Origin Policy:** Browser blocks a page from reading responses from a different origin (scheme+host+port) by default.
**178. CORS:** Server opts into allowing specific cross-origin requests via `Access-Control-Allow-*` headers; some cross-origin requests trigger a browser `OPTIONS` preflight first.

## Part 18 — Modern Web Infrastructure

**179. CDN:** Distributed edge servers cache static content close to users, reducing latency.
**180. Reverse Proxy:** Client sends requests to it; it forwards them to backend server(s). Handles TLS termination, routing, hides internals.
**181. Load Balancer:** Distributes traffic across multiple backend servers per configured algorithm and health status (round robin, least connections, etc.).
**182. WebSocket:** Persistent, full-duplex connection (starts as an HTTP "upgrade"); both client and server can send messages at any time — used for chat/live updates.

## Part 19 — Practical Examples (index only — see complete PDF for full walkthroughs)

1. Typing `https://google.com` → DNS → TCP handshake → TLS → HTTPS request → routing → response.
2. Two devices in a LAN → ARP → switch delivers by MAC, no routing needed.
3. Packet's journey through multiple routers (hop-by-hop, TTL decremented each hop).
4. NAT: private IP → router → shared public IP.
5. ARP: IP → broadcast request → MAC reply.
6. Subnetting: `/24` → four `/26` subnets.
7. TCP handshake: SYN → SYN-ACK → ACK.
8. VPN: device → encrypted tunnel → VPN server → destination (destination sees VPN server's IP, not yours).
9. Full web dev request flow: URL → DNS → routing → TCP → TLS → HTTP request → reverse proxy/load balancer → app server → HTTP response → browser → cookies/caching/rendering.
