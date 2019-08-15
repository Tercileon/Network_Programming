|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## Address Resolution Protocol

![](/assets/arp-discovery-reply-and-caching.png)

ARP: [https://tools.ietf.org/html/rfc826](https://tools.ietf.org/html/rfc826)

EtherType: [http://www.iana.org/assignments/ieee-802-numbers/ieee-802-numbers.xhtml](http://www.iana.org/assignments/ieee-802-numbers/ieee-802-numbers.xhtml)

Address Resolution Protocol \(ARP\) is a protocol for mapping an Internet Protocol address \(IP address\) to a physical machine address that is recognized in the local network. 

For example, in IP Version 4 an address is 32 bits long. In an Ethernet local area network, however, addresses for attached devices are 48 bits long \(The physical machine address is also known as a Media Access Control or MAC address\). A table, usually called the ARP cache, is used to maintain a correlation between each MAC address and its corresponding IP address. ARP provides the protocol rules for making this correlation and providing address conversion in both directions.

## How ARP Works

When an incoming packet destined for a host machine on a particular local area network arrives at a gateway, the gateway asks the ARP program to find a physical host or MAC address that matches the IP address. The ARP program looks in the ARP cache and, if it finds the address, provides it so that the packet can be converted to the right packet length and format and sent to the machine. If no entry is found for the IP address, ARP broadcasts a request packet in a special format to all the machines on the LAN to see if one machine knows that it has that IP address associated with it. A machine that recognizes the IP address as its own returns a reply so indicating. ARP updates the ARP cache for future reference and then sends the packet to the MAC address that replied.

---

|[Next Topic](/04-osi-layer-2/arp-header.md)|
|---|
