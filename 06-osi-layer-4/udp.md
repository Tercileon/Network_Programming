|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## UDP

UDP is connectionless and best effort delivery. Error checking is limited to a UDP checksum.

Being connection-less minimizes overhead.

Removing error checking, reordering, and other nice functionality from TCP increases speed since re-transmissions do not occur and there is no need to wait for acknowledgements.

UDP is particularly well suited to protocols where a single message is sent the responses are also single messages:

* DNS, DHCP, SNMP, RIP, etc...

Protocols and applications designed to handle a high volume of traffic can often internally handle some packet loss:

* VOIP, Streaming Media, Video Games, etc...

---

|[Next Topic](/06-osi-layer-4/udp-header.md)|
|---|
