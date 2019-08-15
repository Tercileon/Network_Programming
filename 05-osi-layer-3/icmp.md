|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## ICMP

The Internet Control Message Protocol is a supporting or "helper" protocol in the Internet protocol suite. It is used by network devices, including routers, to send error messages and operational information indicating, for example, that a requested service is not available or that a host or router could not be reached.

Many messages have been deprecated, reserved, or are obsolete.

Each message has a Type, and each type may have several Codes.

Type 0 Echo Reply:

* Ping

Type 3 Destination Unreachable:

* Code 0 Destination Network Unreachable
* Code 1 Destination Host Unreachable
* Code 3 Destination Port Unreachable \(NOTE: See Layer 4 for slight modification regarding TCP\)

Type 8 - Echo Request:

* Ping

Type 11 Time Exceeded:

* Code 0 TTL Exceeded
* Code 1 Fragment Reassembly Time Exceeded

Type 30 Traceroute:

* Deprecated

---

|[Next Topic](/05-osi-layer-3/ping.md)|
|---|
