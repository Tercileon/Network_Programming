<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" rel="Return to TOC"> Return to TOC </a>

# ARP Header

![](../.gitbook/assets/arp-6-638.jpg)

**Hardware Type** - The physical medium of transmission. 1 for Ethernet, 6 for 802.11 \(wifi\).

**Protocol Type** - Uses same constants as EtherType. Identifies the Layer 3 address that needs to be mapped to an Ethernet address.

**Hardware Address Length** - Size of Layer 2 address defined in Hardware type.

**Protocol Address Length** - Size of Layer 3 address defined in Protocol Type.

**Op Code** - 1 for Request, 2 for Reply. Other codes exist for protocols that make use of an Arp Header

**Sender Hardware Address, Sender Protocol Address** - The sender's addresses.

**Target Hardware Address, Target Protocol Address** - The target's addresses, The hardware address is filled in upon receipt of the ARP Request.

---
<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/04-osi-layer-2/rarp.md" > Continue to Next Topic </a>
