|[Table of Contacts](/00-Table-of-Contents.md)|
|---|

---

## Broadcast vs Collision Domains

![](/assets/data-transfer-domains.jpg)

**Collision domain**

A collision domain is, as the name implies, a part of a network where packet collisions can occur. A collision occurs when two devices send a packet at the same time on the shared network segment. The packets collide and both devices must send the packets again, which reduces network efficiency. Collisions are often in a hub environment, because each port on a hub is in the same collision domain. By contrast, each port on a bridge, a switch or a router is in a separate collision domain.

## **Broadcast domain**

A broadcast domain is a domain in which a broadcast is forwarded. A broadcast domain contains all devices that can reach each other at the data link layer \(OSI layer 2\) by sending a broadcast. All ports on a hub or a switch are by default in the same broadcast domain. All ports on a router are in different broadcast domains and routers don’t forward broadcasts from one broadcast domain to another.

---

|[Next Topic](/04-osi-layer-2/arp.md)|
|---|
