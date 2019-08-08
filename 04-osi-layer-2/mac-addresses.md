<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" rel="Return to TOC"> Return to TOC </a>

# MAC Addresses

48 bits long, usually represented as 6 groups of hex \(e.g.aa:bb:cc:dd:ee:ff\).

Manufacturers 'burn in' a MAC address to each port on a device, however most modern equipment allows the MAC to be changed in software as well.

**Organizational Unique Identifier** - \(OUI\) First 3 bytes.

* OUIs specific to each manufacturer \(VMWare OUI 00:50:56, Intel OUIs 00:02:B3, 00:03:47, 00:04:23\)
* Majority of the time OUIs are enforced. The MAC address of a device will be unique within the network
* LSBit in 1st byte in OUI determines if address is unicast \(0\) or muilticast\(1\)
* 2ndLSBit in 1st byte in OUI determines if the mac is globally unique \(0\), or locally administered \(1\)

**Host ID** - Last 3 bytes

* Randomly decided by manufacturer
* Ideally there are no collisions within a physical network

**Special MAC Addresses**

* The Layer 2 BROADCAST address for IPv4 and ARP is FF:FF:FF:FF:FF:FF
* The Layer 2 MULTICAST address for IPv6 is 33:33:00:00:00:01

---
<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/04-osi-layer-2/switches.md" > Continue to Next Topic </a>
