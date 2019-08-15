|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## IPv4

![](/assets/ethernet-frame-explained.png)

* Version - Set to 4 for IPv4
* Header Length – Size of IP header
* Differentiated Services Code Point \(DSCP\) – Formerly “Type of Service \(TOS\)”, it was redefined by RFC 2474. Used for new technologies that require real time data streamed over the network. We will not deal with this in this class
* Explicit Congestion Notification – Formerly part of TOS, used to indicate network congestion.

##       _\(NOTE: This is not the same as TCP's congestion handling\)_

* Total Length – Size of packet in bytes, including header and data
* Identification – Identifies a group of IP fragments
* Flags – Fragment flags

Bit Indicator RFC 791 Definition

0xx Reserved

x0x May Fragment

x1x Do Not Fragment

xx0 Last Fragment

xx1 More Fragments

from: [http://www.wildpackets.com/resources/compendium/tcp\_ip/ip\_fragmentation](http://www.wildpackets.com/resources/compendium/tcp_ip/ip_fragmentation)

* Fragment offset – offset of fragment from original packet
* Time to Live – Decremented first thing at each hop, packet is discarded when TTL is 0
* Protocol – Protocol used in data portion
* Header checksum – Error Checking
* Source / Destination IP – Do not change during routing

IPv4 has the ability for optional headers, but they are typically not used.

Seeing them in IPv4 is worth an investigation if you are an analyst/admin.

![](/assets/irlvy.jpg)

---

|[Next Topic](/05-osi-layer-3/nat-and-pat.md)|
|---|
