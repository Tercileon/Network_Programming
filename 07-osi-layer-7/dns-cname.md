|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## DNS - CNAME

CNAME records define an alias for canonical name for your server \(one defined by an A or AAAA record\).

For instance, we could have an A name record defining the "server1" host and then use the "www" as an alias for this host:

```text
server1     IN  A       111.111.111.111
www         IN  CNAME   server1
```

According to RFC 2181, there must be only one canonical name per alias.

---

|[Next Topic](/07-osi-layer-7/dns-mx-records.md)|
|---|
