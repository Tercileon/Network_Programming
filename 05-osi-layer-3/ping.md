|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## Ping

Ping is ubiquitous. It shows the connectivity status between two hosts.

It is an example of ICMP used for information purposes.

Host A initiates a request to Host B:

* ICMP Type 8

Host B receives it, and sends a response to A:

* ICMP Type 0

If the packet cannot be delivered to a host, an ICMP message is generated and returned to the sender.

The ICMP Type and Code specifies the error.

Part of the original packet is also included to help the sender know which transmission caused the error.

---

|[Next Topic](/05-osi-layer-3/icmp-errors.md)|
|---|
