<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" > Return to TOC </a>

# Lab 3-1

## TCP Sockets Tutorial in C

![](/assets/image%20%282%29.png)

### TCP Client:

First, import standard and socket related libraries.

```text
#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
```

Next, create the socket. 

A socket, `network_socket`, is created with the _socket_ system call:

```text
int network_socket = socket(domain, type, protocol);
```

All the parameters as well as the return value are integers:

**domain, or address family** —

communication domain in which the socket should be created. Some of address families are `AF_INET (IP)`, `AF_INET6 (IPv6)`, `AF_UNIX (local channel, similar to pipes)`, `AF_ISO (ISO protocols)`, and `AF_NS (Xerox Network Systems protocols)`.

**type** —

type of service. This is selected according to the properties required by the application: `SOCK_STREAM (virtual circuit service)`, `SOCK_DGRAM (datagram service)`, `SOCK_RAW (direct IP service)`. Check with your address family to see whether a particular service is available.

**protocol** —

indicate a specific protocol to use in supporting the sockets operation. This is useful in cases where some families may have more than one protocol to support a given type of service. The return value is a file descriptor \(a small integer\).

 For TCP/IP sockets, we want to specify the IP address family \(`AF_INET`\) and virtual circuit service \(`SOCK_STREAM`\). Since there’s only one form of virtual circuit service, there are no variations of the protocol, so the last argument, _protocol_, is zero. Our code for creating a TCP socket looks like this:

```text
	int network_socket;
	network_socket = socket(AF_INET, SOCK_STREAM, 0);
```

> AF\_INET = IPv4 \| AF\_INET6 = IPv6
>
> SOCK\_STREAM = TCP \| SOCK\_DGRAM = UDP

Now, specify an address for the socket to connect to.

```text
	struct sockaddr_in server_address;  // socket struct called server_address
	server_address.sin_family = AF_INET; // address family
	server_address.sin_port = htons(30001); //converts the unsigned short int from 
		//"host" byte order to "network" byte order. host-to-network(PORT#)
	server_address.sin_addr.s_addr = INADDR_ANY; 
```

sin\_addr is a struct. So you want to access s\_addr within sin.addr 

INADDR\_ANY is the same as 0.0.0.0 basically telling the computer to connect to any available IPv4 address on the computer.

Finally, initiate the connection.

```text
	int connection_status;
	connection_status = connect(network_socket, (struct sockaddr *) &server_address, sizeof(server_address));
	
	//error checking connection to server
	if(connection_status == -1)
	{
		printf("Error with connection\n\n");
	}
```

\#include &lt;sys/types.h&gt;

\#include &lt;sys/socket.h&gt;

int connect\(int sockfd, struct sockaddr \*serv\_addr, int addrlen\);

* sockfd -  A file descriptor that specifies the socket for which the address should be set.
* serv\_addr - A _struct sockaddr_ containing the destination port and IP address.
* addrlen - Defines the length of the address being passed to the function.

If the client connects successfully, receive the information and print it out.

```text
	char server_response[256]; 
	recv(network_socket, &server_response, sizeof(server_response), 0);

	printf("The server sent the data: %s \n", server_response);
```

recv\(socket created, data from server / location, and size\) There is also an optional flags parameter.

Once all of the information has been sent and/or received, close the socket, passing the _network\_socket_ as an attribute to the _close\(\)_ function.

```text
close(network_socket);
```

#### TCP Client

```text
#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>

int main() {	
	
	// create the socket
	int network_socket;
	network_socket = socket(AF_INET, SOCK_STREAM, 0);
	
	//setup an address
	struct sockaddr_in server_address;
	server_address.sin_family = AF_INET;
	server_address.sin_addr.s_addr = INADDR_ANY;
	server_address.sin_port = htons(30001);

	int connection_status;
	connection_status = connect(network_socket, (struct sockaddr *) &server_address, sizeof(server_address));
	
	//error checking connection to server
	if(connection_status == -1)
	{
		printf("Error with connection\n\n");
	}
	
	//receive data from the server
	char server_response[256];
	recv(network_socket, &server_response, sizeof(server_response), 0);

	//print the server's response
	printf("The server sent the data: %s \n", server_response);
	
	close(network_socket);

	return 0;
}
```

## TCP Server

First, load the standard and socket libraries.

```text
#include <stdio.h>
#include <stdlib.h>
#include <sys/socket.h>
#include <sys/types.h>
#include <netinet/in.h>
```

Next, create the socket.

```text
    int server_socket;
    server_socket = socket(AF_INET, SOCK_STREAM, 0);
```

Then, specify an address for the server.

```text
    struct sockaddr_in server_address;
    server_address.sin_family = AF_INET;
    server_address.sin_port = htons(30001);
    server_address.sin_addr.s_addr = INADDR_ANY;
```

The first parameter, `socket`, is the socket that was created with the _socket_ system call.

For the second parameter, the structure `sockaddr` is a generic container that just allows the OS to be able to read the first couple of bytes that identify the address family. The address family determines what variant of the `sockaddr` struct to use that contains elements that make sense for that specific communication type. For IP networking, we use `struct sockaddr_in`, which is defined in the header `netinet/in.h`. This structure defines:

```text
struct sockaddr_in 
{ 
    __uint8_t         sin_len; 
    sa_family_t       sin_family; 
    in_port_t         sin_port; 
    struct in_addr    sin_addr; 
    char              sin_zero[8]; 
};
```

Before calling _bind_, we need to fill out this structure. The three key parts we need to set are:

**sin\_family**

The address family we used when we set up the socket. In our case, it’s `AF_INET`.

**sin\_port**

The port number \(the transport address\). You can explicitly assign a transport address \(port\) or allow the operating system to assign one. If you’re a client and won’t be receiving incoming connections, you’ll usually just let the operating system pick any available port number by specifying port 0. If you’re a server, you’ll generally pick a specific number since clients will need to know a port number to connect to.

**sin\_addr**

The address for this socket. This is just your machine’s IP address. With IP, your machine will have one IP address for each network interface. For example, if your machine has both Wi-Fi and ethernet connections, that machine will have two addresses, one for each interface. Most of the time, we don’t care to specify a specific interface and can let the operating system use whatever it wants. The special address for this is 0.0.0.0, defined by the symbolic constant `INADDR_ANY`.

Since the address structure may differ based on the type of transport used, the third parameter specifies the length of that structure. This is simply `sizeof(struct sockaddr_in)`.

The code to bind and listen on a socket looks like this:

```text
bind(server_socket, (struct sockaddr*) &server_address, sizeof(server_address));
listen(server_socket, 5);
```

Finally, accept the connection and send/receive data.

```text
    int client_socket;
    client_socket = accept(server_socket, NULL, NULL);
    send(client_socket, server_message, sizeof(server_message), 0);
```

After all transmissions have completed, close the socket.

```text
    close(server_socket);
```

#### TCP Server

```text
#include <stdio.h>
#include <stdlib.h>
#include <sys/socket.h>
#include <sys/types.h>
#include <netinet/in.h>

int main() {

    char server_message[256] = "Successfully connected!";
    
    // create the server socket
    int server_socket;
    server_socket = socket(AF_INET, SOCK_STREAM, 0);

    
    // define the server address
    struct sockaddr_in server_address;
    server_address.sin_family = AF_INET;
    server_address.sin_port = htons(30001);
    server_address.sin_addr.s_addr = INADDR_ANY;

    // bind the socket to our specified IP and port
    bind(server_socket, (struct sockaddr*) &server_address, sizeof(server_address));

    listen(server_socket, 5);

    int client_socket;
    client_socket = accept(server_socket, NULL, NULL);
    
    // send the message
    send(client_socket, server_message, sizeof(server_message), 0);

    // close the socket
    close(server_socket);
    
    return 0;
}

```

---

**Complete Performance Lab** 3-2

---

|[Lab 3-2}(/05-osi-layer-3/lab-3.md)|
|---|
