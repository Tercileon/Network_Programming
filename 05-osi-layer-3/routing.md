|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## Routing

Packets are routed independently of each other, even if they are to the same destination.

Traffic destined for a private IP address will not be routed onto the public internet without special configurations.

Broadcast traffic will not be routed outside of that network.

When a router receives a packet, the destination IP of a packet is compared to the networks in the routing table.

* If the network is directly connected, send the packet to that network.
* If the network is known, but not connected, send it to the NEXT HOP specified in the routing table with the 'best' weight.
* Otherwise send it to the DEFAULT GATEWAY.

---

|[Next Topic](/05-osi-layer-3/ipv4.md)|
|---|
