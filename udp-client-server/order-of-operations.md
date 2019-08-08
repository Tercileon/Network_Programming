# Order of Operations

* **socket\(\)** – Get a socket descriptor
* **bind\(\)** – Specify SOURCE port \(Optional for client/sender, Mandatory server/reciever\)
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

