|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## SOA Records

The **Start of Authority**, or SOA, record identifies information about the domain and is a mandatory record in all zone files. It must be the first real record in a file \(although $ORIGIN or $TTL specifications may appear above\). It is also one of the most complex.

This also serves as the authoritative copy that keeps secondary DNS servers up to date.

```text
domain.com.  IN SOA ns1.domain.com. admin.domain.com. (                                            
                                12083   ; serial number
                                3h      ; refresh interval
                                30m     ; retry interval
                                3w      ; expiry period
                                1h      ; negative TTL
)
```

In addition to the DNS record fields, it contains more information:

**Authoritative server** - Primary DNS for the zone.

**Responsible Person** - Email address of admin, with @ replaced by .

**Serial Number** - Current "version number", used by secondary DNS to determine whether they should update.

**Refresh** - Number of seconds between each secondary DNS checks for updates.

**Retry** - Number of seconds to wait for secondary DNS to re-try a zone transfer.

**Expire** - TTL of zone transfer for secondary DNS.

**Minimum TTL** - The minimum TTL for all records in the zone.**domain.com.**: This is the root of the zone. This specifies that the zone file is for the `domain.com.` domain. Often, you'll see this replaced with `@`, which is just a placeholder that substitutes the contents of the `$ORIGIN` variable we learned about above.

* **IN SOA**: The "IN" portion means internet \(and will be present in many records\). The SOA is the indicator that this is a Start of Authority record.
* **ns1.domain.com.**: This defines the primary master name server for this domain. Name servers can either be master or slaves, and if dynamic DNS is configured one server needs to be a "primary master", which goes here. If you haven't configured dynamic DNS, then this is just one of your master name servers.
* **admin.domain.com.**: This is the email address of the administrator for this zone. The "@" is replaced with a dot in the email address. If the name portion of the email address normally has a dot in it, this is replace with a "\" in this part \([your.name@domain.com](mailto:your.name@domain.com) becomes your\name.domain.com\).
* **12083**: This is the serial number for the zone file. Every time you edit a zone file, you must increment this number for the zone file to propagate correctly. Slave servers will check if the master server's serial number for a zone is larger than the one they have on their system. If it is, it requests the new zone file, if not, it continues serving the original file.
* **3h**: This is the refresh interval for the zone. This is the amount of time that the slave will wait before polling the master for zone file changes.
* **30m**: This is the retry interval for this zone. If the slave cannot connect to the master when the refresh period is up, it will wait this amount of time and retry to poll the master.
* **3w**: This is the expiry period. If a slave name server has not been able to contact the master for this amount of time, it no longer returns responses as an authoritative source for this zone.
* **1h**: This is the amount of time that the name server will cache a name error if it cannot find the requested name in this file

---

|[Next Topic](/07-osi-layer-7/dns-a-and-aaaa-records.md)|
|---|
