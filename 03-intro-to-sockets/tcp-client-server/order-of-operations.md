|[Table of Contacts](/00-Table-of-Contents.md)|
|---|

---

## Order of Operations

![](/assets/image%20%2813%29.png)

## TCP Client Order of Operations

* **socket\(\)** – Get a socket descriptor
* **bind\(\)** – Specify SOURCE port \(Optional\)
* **connect\(\)** – Connect to destination IP/PORT
* **send\(\)/recv\(\)** – Data transfer
* **close\(\)** – Close the socket

## TCP Server Order of Operations

* **socket\(\)** – Get a socket descriptor
* **bind\(\)** – Specify SOURCE port to listen on \(Mandatory\)
* **listen\(\)** – Wait for a client to connect on the port
* **accept\(\)** – Returns a tuple containing the NEW socket to communicate with a single client, and a tuple of remote ip/port 
* **send/recv\(\)** – Data Transfer
* **close\(\)** – Close the socket

### Multiple Assignment:

`ret = sock.accept()`

`ret[0] # The socket`

`ret[1] # tuple of remote ip/port`

`accept_socket, remote = sock.accept`

---

|[Next Topic](/03-intro-to-sockets/tcp-client-server/sendall.md)|
|---|
