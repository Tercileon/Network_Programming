|[Table of Contacts](/00-Table-of-Contents.md)|
|---|

---

## BSD Socket API

* **Internet Protocol Suite**

![](/assets/ip_stack_connections.svg.png)

[https://en.wikipedia.org/wiki/Internet\_protocol\_suite](https://en.wikipedia.org/wiki/Internet_protocol_suite)

![](/assets/internet-socket.png)

Sockets are the abstraction that allow applications to communicate with each other. Socket programming allows us to control the functionality of the interface between ports and applications. Another way to think of them, is they're a way to speak to other programs using standard Unix file descriptors. Since everything in Unix/Linux is a file.

A file descriptor is simply an integer associated with an open file. But, that file can be a network connection, a F/IO, a pipe, a terminal, a real on-the-disk file, or just about anything else. Everything in Unix is a file! So when you want to communicate with another program over the Internet you're gonna do it through a file descriptor.

Just like using **read\(\)** and **write\(\) calls** to communicate with a file. You make a call to the  **socket\(\)** system routine. It returns the socket descriptor, and you communicate through it using the specialized **send\(\)** and **recv\(\)** socket calls.

**Berkeley sockets**  are an[ application programming interface](https://en.wikipedia.org/wiki/Application_programming_interface) \(API\) for [Internet sockets](https://en.wikipedia.org/wiki/Internet_socket) and[ Unix domain sockets](https://en.wikipedia.org/wiki/Unix_domain_socket), used for [inter-process communication](https://en.wikipedia.org/wiki/Inter-process_communication) \(IPC\). It is commonly implemented as a[ library](https://en.wikipedia.org/wiki/Library_%28computing%29) of linkable modules. It originated with the 4.2 BSD [Unix](https://en.wikipedia.org/wiki/Unix) released in 1983.

Berkeley sockets evolved with little modification from a [de facto standard](https://en.wikipedia.org/wiki/De_facto_standard) into a component of the[ POSIX](https://en.wikipedia.org/wiki/POSIX) specification. Therefore, the term  **POSIX sockets**  is essentially synonymous with **Berkeley sockets**. They are also known as **BSD sockets**, acknowledging the first implementation in the [Berkeley Software Distribution](https://en.wikipedia.org/wiki/Berkeley_Software_Distribution).

[https://en.wikipedia.org/wiki/Berkeley\_sockets](https://en.wikipedia.org/wiki/Berkeley_sockets)

* **We will be using the BSD Socket API for networking**
* **Knowing BSD sockets will provide a foundation to do networking in almost any language/environment**
* **Default socket API is a string-based protocol**

\(Even Windows' Winsock library still follows the call pattern, even if Microsoft makes their function calls take a dozen more parameters\)

Part of the trouble with understanding network programming is that a “socket” can mean a number of subtly different things, depending on context. So first, let’s make a distinction between a “client” socket - an endpoint of a conversation, and a “server” socket, which is more like a switchboard operator. The client application \(your browser, for example\) uses “client” sockets exclusively; the web server it’s talking to uses both “server” sockets and “client” sockets.

---

|[Next Topic](/03-intro-to-sockets/bsd-socket-api/socket-types.md)|
|---|
