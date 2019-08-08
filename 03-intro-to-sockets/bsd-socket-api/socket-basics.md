<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" rel="Return to TOC"> Return to TOC </a>

# Socket Basics

**Reference:** [https://docs.python.org/2/library/socket.html?highlight=pton\#module-socket](https://docs.python.org/2/library/socket.html?highlight=pton#module-socket)

## **To create a socket:**

#### _import socket_ 

### _s = socket.socket\(addr\_family, type\)_

* **Address Families:**

### _socket.AF\_INET      Internet protocol \(IPv4\)_ 

### _socket.AF\_INET6     Internet protocol \(IPv6\)_ 

* **Socket Types:**

### _socket.SOCK\_STREAM  Connection based stream \(TCP\)_ 

### _socket.SOCK\_DGRAM   Datagrams \(UDP\)_

## Creating a socket is only the ﬁrst step

### _s = socket\(AF\_INET, SOCK\_STREAM\)_ 

**Further use depends on application** 

* **Server** - Listen for incoming connections 
* **Client** - Make an outgoing connection

**TCP Server code will deal with TWO \(or more\) sockets**

* The first socket is created by socket\(\) and is used to LISTEN
* The other sockets are returned by accept\(\) after a client connects to the listening socket. This new socket is used for data transfer to that specific client
* Accept\(\) returns two values, the socket, and the IP of the other side.

**Keep in mind**

* Calls to accept\(\) will NOT alter the LISTENING socket
* By default, accept\(\) will block until a connection is received

---
<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/03-intro-to-sockets/udp-client-server/README.md" > Continue to Next Topic </a>
