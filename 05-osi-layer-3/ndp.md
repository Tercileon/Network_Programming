|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## NDP

Neighbor Discovery Protocol is a collection of ICMPv6 messages for auto configuration, discovery, and awareness.

NDP uses the ICMP Header format. If you compare the ICMP header to that of the RFC4861 you will notice similarities.

Read the RFC! It tells you how to fill out values in previous headers!

**Neighbor Solicitations** - Map a known IPv6 address to a layer 2 address

**Neighbor Advertisements** - Sent in response to a Neighbor Solicitation or you can broadcast your own layer 2 address to the network unsolicited

**Router Solicitation** - Request a Router Advertisement

**Router Advertisements** - Sent in response to a Router Solicitation. It basically says here are all networks I know about.

* An RA also tells you if the sender is the first hop for that network, or if the network is actually considered "on-link" \(i.e. directly connected because multiple prefixes on the same LAN\)

**Redirect** - If you see traffic destined somewhere, and you know a better route to a given host you can send this to have the sender redirect their traffic

---

|[Next Topic](/05-osi-layer-3/icmp.md)|
|---|
