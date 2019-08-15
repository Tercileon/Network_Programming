|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## DNS - MX Records

MX records are used to define the mail exchanges that are used for the domain. This helps email messages arrive at your mail server correctly.

Unlike many other record types, mail records generally don't map a host to something, because they apply to the entire zone. As such, they usually look like this:

```text
        IN  MX  10  mail1.domain.com.
        IN  MX  50  mail2.domain.com.
mail1   IN  A       111.111.111.111
mail2   IN  A       222.222.222.222
```

Note that there is no host name at the beginning.

Also note that there is an extra number in there. This is the preference number that helps computers decide which server to send mail to if there are multiple mail servers defined. Lower numbers have a higher priority.

The MX record should generally point to a host defined by an A or AAAA record, and not one defined by a CNAME.

In this example, the "mail1" host is the preferred email exchange server.

We could also write that like this:

```text
        IN  MX  10  mail1
        IN  MX  50  mail2
mail1   IN  A       111.111.111.111
mail2   IN  A       222.222.222.222
```

---

|[Next Topic](/07-osi-layer-7/dns-srv-records.md)|
|---|
