|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## DNS - SRV Records

These allow domains to identify the services offered and the hosts responsible for providing the services:

**Service** - name of the service \(http, telnet, etc\)

**Proto** - Usually the Layer 4 protocol

**Domain** - Domain this applies to

**TTL/Class** - Same as other DNS records

**Priority** - Lower number = higher priority. Higher priortity hosts get contacted first

**Weight** - Used to load balance hosts with identical Priorities

**Port** - Port of service

**Target** - FQDN for service host

### `_http._tcp.reskit.com. IN SRV 0 0 80 webserver1.noam.reskit.com.`

### `_http._tcp.reskit.com. IN SRV 10 0 80 webserver2.noam.reskit.com.`

---

|[Next Topic](/07-osi-layer-7/dns-resolution.md)|
|---|
