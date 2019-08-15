|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## SocketServer

The SocketServer module is a framework for creating network servers. It defines classes for handling synchronous network requests \(the server request handler blocks until the request is completed\) over TCP, UDP, Unix streams, and Unix datagrams. It also provides mix-in classes for easily converting servers to use a separate thread or process for each request, depending on what is most appropriate for your situation.

Responsibility for processing a request is split between a server class and a request handler class. The server deals with the communication issues \(listing on a socket, accepting connections, etc.\) and the request handler deals with the “protocol” issues \(interpreting incoming data, processing it, sending data back to the client\). This division of responsibility means that in many cases you can simply use one of the existing server classes without any modifications, and provide a request handler class for it to work with your protocol.

### Server Types

There are five different server classes defined in SocketServer. BaseServer defines the API, and is not really intended to be instantiated and used directly. TCPServer uses TCP/IP sockets to communicate. UDPServer uses datagram sockets. UnixStreamServer and UnixDatagramServer use Unix-domain sockets and are only available on Unix platforms.

### Server Objects

To construct a server, pass it an address on which to listen for requests and a request handler _class_ \(not instance\). The address format depends on the server type and the socket family used. Refer to the socket module documentation for details.

Once the server object is instantiated, use either handle\_request\(\) or serve\_forever\(\) to process requests. The serve\_forever\(\) method simply calls handle\_request\(\) in an infinite loop, so if you need to integrate the server with another event loop or use select\(\) to monitor several sockets for different servers, you could call handle\_request\(\) on your own. See the example below for more detail.

### Implementing a Server

If you are creating a server, it is usually possible to re-use one of the existing classes and simply provide a custom request handler class. If that does not meet your needs, there are several methods of BaseServer available to override in a subclass:

* verify\_request\(request, client\_address\) - Return True to process the request or False to ignore it. You could, for example, refuse requests from an IP range if you want to block certain clients from accessing the server.
* process\_request\(request, client\_address\) - Typically just calls finish\_request\(\) to actually do the work. It can also create a separate thread or process, as the mix-in classes do \(see below\).
* finish\_request\(request, client\_address\) - Creates a request handler instance using the class given to the server’s constructor. Calls handle\(\) on the request handler to process the request.

### Request Handlers

Request handlers do most of the work of receiving incoming requests and deciding what action to take. The handler is responsible for implementing the “protocol” on top of the socket layer \(for example, HTTP or XML-RPC\). The request handler reads the request from the incoming data channel, processes it, and writes a response back out. There are 3 methods available to be over-ridden.

* setup\(\) - Prepare the request handler for the request. In the StreamRequestHandler, for example, the setup\(\) method creates file-like objects for reading from and writing to the socket.
* handle\(\) - Do the real work for the request. Parse the incoming request, process the data, and send a response.
* finish\(\) - Clean up anything created during setup\(\).

In many cases, you can simply provide a handle\(\) method.

#### Reference: [https://docs.python.org/2/library/socketserver.html](https://docs.python.org/2/library/socketserver.html)

---

|[Next Topic](/08-advanced-functionality/socketserver/example.md)|
|---|
