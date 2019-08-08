<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" > Return to TOC </a>

# IPv6 Addresses

IPv6 addresses are 128 bits long and represented by groups of 1-4 hex characters separated by a **:** \(aka a "hextet“, or more formally a “hexadectet”\).

* 2001:0db8:0000:0000:0000:ff00:0042:8329

Using the recommendations in RFC5952 section 4.2 we can shorten that IPv6 address.

Leading 0's in a grouping may be omitted.

* 2001:db8:0:0:0:ff00:42:8329

It may contain at MOST a single :: which represents the largest contiguous block \(longer than 16 bits\) of 0's in the address

* 2001:db8::ff00:42:8329 

If multiple contiguous blocks are the same length, shorten the left most one

* 2001:0:0:AAAA:0:0:B:CC becomes 2001::AAAA:0:0:B:CC

If the contiguous 0's only encompass a single hextet, do NOT replace it with a ::

* The 2nd hextet in A:0:BBBB:CCC:D0:22:FF:4412 should never be reduced with a ::

The Layer 2 \(Ethernet\) multicast address for IPv6 is 33:33:00:00:00:01

---
<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/05-osi-layer-3/ipv6-address-types.md" > Continue to Next Topic </a>
