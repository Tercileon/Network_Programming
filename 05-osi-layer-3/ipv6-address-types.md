<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" > Return to TOC </a>

# IPv6 Address Types

Generally there are three types of addresses:

* Unicast
* Multicast
* Anycast

There are also several scopes:

* Global \("Public" in IPv4\)
* Site Local \("Private" in IPv4\)
* Link Local

There is no IPv6 broadcast address. Multicast addresses fulfill that role.

The type of address is specified by the value of the first hextet.

| IPv6 | Description | IPv4 Equivalent |
| :--- | :--- | :--- |
| ::/128 | Uspecified/Default | 0.0.0.0 |
| ::1/128 | Loopback | 127.0.0.1 |
| fec0::/7 | Site Local, not routed | 10.0.0.0/8, 192.168.0.0/16 |
| fe80::/10 | Link Local, not routed | 169.254.0.0/16 |
| ff00::/8 | Multicast | Class D |
| 2001::/32 | Teredo, Allows IPv6 over IPv4 | n/a |
| 2002::/16 | 6 to 4, Allows IPv6 over IPv4 | n/a |

NOTE: This list is not exhaustive.

[http://www.iana.org/assignments/ipv6-multicast-addresses/ipv6-multicast-addresses.xhtml](http://www.iana.org/assignments/ipv6-multicast-addresses/ipv6-multicast-addresses.xhtml)

---

<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/05-osi-layer-3/unicast.md" > Continue to Next Topic </a>
