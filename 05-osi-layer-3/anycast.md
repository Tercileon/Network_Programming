|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## Anycast

Anycast addressing does not operate like traditional addressing.

Anycast addresses are in the global unicast range. The same global unicast address is assigned to multiple interfaces \(perhaps on several different nodes\).

Traffic destined to the anycast address will be delivered to the "nearest" host with that address. It's a trick to rely on a routing protocol which determines the "closest" host that was configured with the address.

Don't use an anycast address as a source address.

This seems strange. Why do it?

Some services are run on multiple servers \(DNS or NTP for example\). You would assign anycast addresses where multiple servers provide the same service but only one reply is required to use the service.

---

|[Next Topic](/05-osi-layer-3/ndp.md)|
|---|
