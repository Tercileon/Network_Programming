<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" rel="Return to TOC"> Return to TOC </a>

# Order of Operations

![UDP Client/Server](../../.gitbook/assets/udpfuncdiag.png)

* **socket\(\)** – Get a socket descriptor
* **bind\(\)** – Specify SOURCE port \(Optional for client/sender, Mandatory server/receiver\)
* **sendto\(\)/recvfrom\(\)** – _Data transfer\*_
* **close\(\)** – Close the socket

\(A UDP socket exists independently of any specific remote IP/PORT\)

* Both sending and receiving data occur on the same socket, even to/from different remote hosts.

You must track the source of incoming data and destination of outgoing data

* This info must be passed to **sendto\(\)** and is returned by **recvfrom\(\)**

It's usually easier to think of them as **"Senders"** and **"Receivers“**.

* If you want to receive traffic, you need bind to a port.

**recvfrom\(\)** returns a tuple of TWO values, the data and a tuple of remote ip/port.

**sendto\(\)** takes a tuple of TWO arguments, data and a tuple of the remote ip/port.

Use the client IP from **recvfrom\(\)** in the call to **sendto\(\)** to return data to that host.

You may use multiple assignments here as well:

### _data, remote = sock.recvfrom\(\)_

## Multiple Assignment:

`ret = sock.recvfrom()`

`ret[0] # The data`

`ret[1] # tuple of remote ip/port`

`data, remote = sock.recvfrom()`

---
<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/03-intro-to-sockets/tcp-client-server/README.md" > Continue to Next Topic </a>
