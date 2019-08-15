|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## DNS – PTR Records

The PTR records are used to define a name associated with an IP address. PTR records are the inverse of an A or AAAA record. PTR records are unique in that they begin at the `.arpa` root and are delegated to the owners of the IP addresses. The Regional Internet Registries \(RIRs\) manage the IP address delegation to organization and service providers. The Regional Internet Registries include APNIC, ARIN, RIPE NCC, LACNIC, and AFRINIC.

Here is an example of a PTR record for 111.222.333.444 would look like:

```text
444.333.222.111.in-addr.arpa.   33692   IN  PTR host.example.com.
```

This example of a PTR record for an IPv6 address shows the _nibble_ format of the reverse of Google's IPv6 DNS Server `2001:4860:4860::8888`

```text
8.8.8.8.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.6.8.4.0.6.8.4.1.0.0.2.ip6.arpa. 86400IN PTR google-public-dns-a.google.com.
```

## There are several things of note:

* **The IP is backwards.**
* **The string 'in-addr.arpa.' is appended to the reversed IP.**
* **'in-addr.arpa.' ends with a . \(meaning it's the fully qualified domain name\)**
* **The IPv6 address is not in a traditional format**  [**http://rdns6.com/hostRecord**](http://rdns6.com/hostRecord%29%29%29%29%20\)

---

|[Next Topic](/07-osi-layer-7/dns-cname.md)|
|---|
