<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" rel="Return to TOC"> Return to TOC </a>

# Routing Protocols

#### Routers operate on Layer 3.

They ignore Layer 2 addresses for decision making.

* Multiple Collision Domains
* Multiple Broadcast Domains

Routing protocols allow neighboring routers to collaborate dynamically.

There are two main types: distance-vector and link-state. 

**Interior gateway protocols type 1**, _**link-state**_ routing protocols, such as OSPF and IS-IS

**Interior gateway protocols type 2**, _**distance-vector**_ routing protocols, such as Routing Information Protocol, RIPv2, IGRP and EIGRP.

**Distance-vector** protocols attempt to calculate the "distance" between networks. Usually this is the total number of hops, or the sum of all weights on a path.

**Link-state** protocols are more concerned with speed and current state of the connections. A longer path with a faster travel time will be prioritized over a path with less hops.

Hybrid protocols also exist.

Each routing protocol defines the metric\(s\) used to calculate _weights_.

The _**“best”**_ weight is used by a router to decide where to send the packet. Weights are usually represented as an integer, and the lowest number is considered best.

**Weights** are calculated individually on each router for each known network. The weight for the exact same network may be different on different routers.

Routers have routing tables that map a **NETWORK**, **WEIGHT**, and the **NEXT HOP ADDRESS**.

Routing tables are populated by the information exchanges dictated by the specific routing protocol being used on that router and it's neighbors.

* Neighbors advertise what NETWORKS they know about, and their WEIGHTS.
* The NEXT HOP will either be the IP of the router that advertised the best path to a destination, OR it will be the locally connected network.

Static routes may also be set, with arbitrary weights, by a network administrator.  

---
<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/05-osi-layer-3/routing.md" > Continue to Next Topic </a>
