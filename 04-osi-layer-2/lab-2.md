|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## Lab 2-2

## Address in Use

If you encounter an error **"Address in use"**, set the following socket option on your sockets \(both client and server\).

### `mysock.setsockopt(socket.SOL_SOCKET,socket.SO_REUSEADDR, 1)`

You may have to wait out the initial timer \(or change your ports\).

### See Also: _Reusing Socket Addresses_ in _Advanced Functionality._

## **Lab 2A**

Write a TCP server that receives a string, reverses order of the words, and sends it back to the client.

Write a TCP client to connect to print the response \(build in IPv4\).

## **Lab 2B**

Write a UDP sender that takes a dictionary, turns it into a JSON string, and sends it to a listener.

Write the UDP receiver to receive the JSON string and turns it back into a dictionary.

Validate by printing the type of your dictionary variable \(build in IPv4\).

## **Lab 2C**

Write a simple socket program that will send back your machine's Host name and IP Address.

\(Don't forget to use your resources \(Pydocs, Man pages\). You can also get formatting help from the python interpreter by using help\(socket.gethostname\) and help\(socket.gethostbyname\) after importing the socket library.\)

## **Lab 2D**

Write a simple socket program that will ask a user to enter a domain and pull the IP address from a remote website. Then use gethostbyaddr\(\) to pull name information.

[https://docs.python.org/2/library/socket.html](https://docs.python.org/2/library/socket.html)

{% embed data="{\"url\":\"http://man7.org/linux/man-pages/man3/gethostbyname.3.html\",\"type\":\"link\",\"title\":\"gethostbyname\(3\) - Linux manual page\"}" %}

## Bonus:  

#### Create an ARP Request using Raw Sockets.

---

|[Next Topic](/05-osi-layer-3/README.md)|
|---|

