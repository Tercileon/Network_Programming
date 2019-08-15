|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## DNS – A and AAAA Records

Both of these records map a host to an IP address. The "A" record is used to map a host to an IPv4 IP address, while "AAAA" records are used to map a host to an IPv6 address.

The general format of these records is this:

```text
host     IN      A       172.16.48.1 (IPv4_address)
```

```text
host     IN      AAAA    2001:db8::ff00:42:8329 (IPv6_address)
```

---
|[Next Topic](/07-osi-layer-7/dns-ptr-records.md)|
|---|
