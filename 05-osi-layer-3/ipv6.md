|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## IPv6

IPv6 is the latest version. It returns to the cleaner design of IP that IPv4 had before attempts to curb exhaustion happened.

Differences from IPv4:

* Back to single address per host, address translation is no longer needed
* Multicasting, QoS, IPSec, and Encryption is built in
* IPv6 can auto-configure itself in a local network

![](/assets/ip4-vs-ip6.png)

Version \(4 bits\) – Set 6 for IPv6.

Traffic Class \(8 bits\) – Categorizes traffic forQoSpurposes. ECN is last 3 bits..

Flow Label \(20 bits\) – Request special handling by routers. May not be honored.

Payload Length \(16 bits\) – Size of payload in OCTETS. Including any extension headers.

Next Header \(8 bits\) – Layer 4 header of payload. Uses same values as IPv4's protocol field.

Hop Limit \(8 bits\) – Same as TTL.

Source / Destination \(128 bits\) - Do not change during routing.

#### IPv6 Headers are identified by number. They are not required to be used, however they provide useful features that were absent or poorly implemented in IPv4.

0 = Hop-by-Hop Options - Options that need to be examined by all devices on the path.

60 = Destination Options \(before routing header\) - Options that need to be examined only by the destination of the packet.

43 = Routing - Methods to specify the route for a datagram \(used with Mobile IPv6\).

44 = Fragment - Contains parameters for fragmentation of datagrams.

51 = Authentication Header \(AH\) - Contains information used to verify the authenticity of most parts of the packet.

50 = Encapsulating Security Payload \(ESP\) - Carries encrypted data for secure communication.

135 = Mobility \(currently without upper-layer header\) - Parameters used with Mobile IPv6.

---

|[Next Topic](/05-osi-layer-3/ipv6-addresses.md)|
|---|
