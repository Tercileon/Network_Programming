|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## Layer 4 Devices

The Transport Layer controls the reliability of communications through flow control, segmentation, and error control, such as: TCP and UDP. Layer 4 devices are also focused specifically on reliable packet transmission.  Gateways and Firewalls can be considered devices of Layers 4 - 7.

**Layer 4 Switches** - Perform policy-based switching which limits traffic types and prioritizes packets based on application.  This allows the switches to tear down and rebuild packets to optimize the flow of traffic.

**Application \(Web\) Accelerators** - Reduce website access time.  They can be a self-contained hardware appliance or installable software utilizing many different techniques:

*  cache recently or frequently accessed documents
*  preemptively resolve hostnames present in a document
*  prefetch and compress documents
*  filter out ads and other undesirable objects

**WAN Accelerators** -  Most operate by first identifying the application via TCP port and then by breaking down, optimizing, and the rebuilding the TCP session as it passes through and between the WAN optimizers.

**Load Balancers** - Refers to efficiently distributing incoming network traffic across a group of backend servers, also known as a server farm or server pool. Load balancing aims to optimize resource use, maximize throughput, minimize response time, and avoid overload of any single resource.

---

|[Next Topic](/06-osi-layer-4/tcp-header-and-flags.md)|
|---|
