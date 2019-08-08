<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" rel="Return to TOC"> Return to TOC </a>

# MTU and Fragmentation

Maximum Transmission Unit is the maximum size of the payload on a given link-layer \(Layer 2\) protocol. \(1500 bytes for Ethernet\).

The max size of an IP packet is 65535 bytes \(unless jumbogram extension header is used\).

IP packets that are bigger than the link-layer protocol MTU are FRAGMENTED into several frames, and the recipient is responsible for reassembly.

MTU can vary at each hop. This means it is possible for every node on the path to the destination to further fragment.

* Senders usually try to discover the smallest MTU on the path and shrink  their own transmissions appropriately.

Packets larger than MTU are dropped and an ICMP message is returned to the sender indicating the packet is too big.

---
<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/04-osi-layer-2/broadcast-vs-collision-domains.md" > Continue to Next Topic </a>
