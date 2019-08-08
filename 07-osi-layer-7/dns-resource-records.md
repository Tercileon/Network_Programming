<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" > Return to TOC </a>

# DNS Resource Records

Within a zone file, records are kept. In its simplest form, a record is basically a single mapping between a resource and a name. These can map a domain name to an IP address, define the name servers for the domain, define the mail servers for the domain, etc.

## Resource Record Types

Different types of records contain different types of host information. For example, an Address record provides the name-to-address mapping for a given host, while a Start of Authority \(SOA\) record specifies the start of authority for a given zone.

A DNS zone must contain several types of resource records for DNS to function properly. Other records can be present, but the following are required for standard DNS:

* **Name server \(NS\)**---Binds a domain name with a hostname for a specific name server The DNS zone must contain NS records for each primary and secondary name server in the zone. The DNS zone must contain NS records to link the zone to higher- and lower-level zones within the DNS hierarchy.
* **Start of Authority \(SOA\)**---Indicates the start of authority for the zone. The name server must contain one SOA record specifying its zone of authority.
* **Canonical name \(CNAME\)**---Specifies the canonical or primary name for the owner. The owner name is an alias.
* **Address \(A\)**---Provides the IP address for the zone.

| RR Type | Field Differences |
| :--- | :--- |
| A | IPv4 Address, eDirectory context, comments, and version |
| AAAA | IPV6 address |
| AFSDB | Subtype and hostname fields |
| CNAME | Domain name of aliased host |
| HINFO | CPU and OS fields of up to 256 characters each |
| ISDN | ISDN address and subaddress fields |
| MB | Mailbox address domain name |
| MG | Mail group member domain name |
| MINFO | Responsible mailbox and error message mailbox |
| MR | Mail rename mailbox |
| MX | Reference and exchange fields |
| NS | DNS server domain name |
| PTR | Domain Name |
| PX | Preference, Map 822 \(domain name\), and Map x400 fields \(domain name in X.400 syntax\) |
| RP | Responsible person's mailbox and TXT RR domain name |
| RT | Preference and Intermediate fields |
| SRV | Service, proto, priority, weight, port, and target fields |
| TXT | Text field for up to 256 characters in multiple strings |
| WKS | Protocol and bit map fields |
| X25 | PSDN address |

## DNS Record Format

**Owner** - Name of domain

**TTL** - TTL in seconds

**Class** - Protocol family to use, almost always IN

**Type** - Type of record being returned

**RDATA** - Data of the record

---

<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/07-osi-layer-7/soa-records.md" > Continue to Next Topic </a>
