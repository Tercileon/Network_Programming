|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## DNS Servers

The system is very simple at a high-level overview, but is very complex as you look at the details. Overall though, it is a very reliable infrastructure that has been essential to the adoption of the internet as we know it today.

### Root Servers

The Internet root name servers manage DNS server information for the Web's top-level domains \(TLD\) \(like ".com" and ".uk"\), specifically the names and IP addresses of the original \(called _authoritative_\) DNS servers responsible for answering queries about each TLD individually.

There are currently 13 root servers in operation. However, as there are an incredible number of names to resolve every minute, each of these servers is actually mirrored. The interesting thing about this set up is that each of the mirrors for a single root server share the same IP address. When requests are made for a certain root server, the request will be routed to the nearest mirror of that root server. DNS servers are installed and maintained by private businesses and Internet governing bodies around the world. Similarly, organizations can deploy DNS on their private networks separately, on the smaller scale.

If a request for "www.wikipedia.org" is made to the root server, the root server will not find the result in its records. It will check its zone files for a listing that matches "www.wikipedia.org". It will not find one.

It will instead find a record for the "org" TLD and give the requesting entity the address of the name server responsible for "org" addresses.

### TLD Servers {#tld-servers}

The requester then sends a new request to the IP address \(given to it by the root server\) that is responsible for the top-level domain of the request.

So, to continue our example, it would send a request to the name server responsible for knowing about "org" domains to see if it knows where "www.wikipedia.org" is located.

Once again, the requester will look for "www.wikipedia.org" in its zone files. It will not find this record in its files.

However, it will find a record listing the IP address of the name server responsible for "wikipedia.org". This is getting much closer to the answer we want.

### Domain-Level Name Servers {#domain-level-name-servers}

At this point, the requester has the IP address of the name server that is responsible for knowing the actual IP address of the resource. It sends a new request to the name server asking, once again, if it can resolve "www.wikipedia.org".

The name server checks its zone files and it finds that it has a zone file associated with "wikipedia.org". Inside of this file, there is a record for the "www" host. This record tells the IP address where this host is located. The name server returns the final answer to the requester.

### Resolving Name Server

When a DNS request is made it is usually sent to a Resolving Name Server. They are intermediaries for the users with cached queries to resolve addresses quickly. If the request is not cached, it is then passed to the Root Servers and proceeds to go through the process of "resolving" the request.

### Zone Files

A zone file is a simple text file that contains the mappings between domain names and IP addresses. This is how the DNS system finally finds out which IP address should be contacted when a user requests a certain domain name.

Zone files reside in name servers and generally define the resources available under a specific domain, or the place that one can go to get that information.

However, don't confuse Zones with Domains, a zone will start as a storage for a single DNS domain name. If you add other domains below the domain where the zone was created, these domains can either be part of the same zone or belong to another zone. If you add a subdomain, the subdomain can either be included and managed as part of the original zone record, or delegated to another zone created for the subdomain.

---

|[Next Topic](/07-osi-layer-7/dns-resource-records.md)|
|---|
