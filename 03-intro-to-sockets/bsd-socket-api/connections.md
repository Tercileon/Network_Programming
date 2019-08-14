|[Table of Contacts](/00-Table-of-Contents.md)|
|---|

---

## **Connections**

### In order to connect to another host, you need to make a socket. To do so, you need to know 2 things:

* The type of address.
* The type of data being transmitted.

  ![](../../.gitbook/assets/sock_con.PNG)

### Each endpoint of a network connection is always represented by a host and port

* In Python you write it out as a tuple \(host,port\)

\("www.python.org",80\)

\("205.172.13.4",443\)

* In almost all of the network programs you’ll write, you use this convention to specify a network address

## **The Address Family**

The type of address determines the "address family". We typically use IPv4 or IPv6, though many others exist. For IPv4 and IPv6 we will use the following constants:

* AF\_INET
* AF\_INET6

In python, these are constants defined as part of the socket module.

---

|[Next Topic]|/03-intro-to-sockets/bsd-socket-api/client-server-model.md|
|---|
