|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## Switches

Switches operate using MAC addresses found in the Ethernet header of the traffic.

Switches have CAM \(Content Addressable Memory\) tables that map a physical port to MAC addresses.

* Switches populate a CAM table by looking at the Ethernet header and determining the SOURCE address of traffic arriving on that port.
* It is possible the table maps multiple MAC Addresses to the same physical port \(e.g. Switch port is connected to a hub with multiple hosts\).

Switches check the DESTINATION MAC address against the MAC table.

* If the address is mapped to a port, forward it out that port.
* If no mapping, forward it out ALL ports EXCEPT the one it was received on - Traffic usually gets a response, and the MAC table will be updated normally when that traffic is seen.

If the DESTINATION MAC is a broadcast address, then forward it out ALL ports EXCEPT the one it was received on.

---

|[Next Topic](/04-osi-layer-2/ethernet-header.md)|
|---|
