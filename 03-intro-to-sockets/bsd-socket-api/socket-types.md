<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" rel="Return to TOC"> Return to TOC </a>

# Socket Types

**There are two basic types of communication** 

* Streams \(TCP\):  Computers establish a connection with each other and read/write data in a continuous stream of bytes---like a ﬁle.  This is the most common. 
* Datagrams \(UDP\): Computers send discrete packets \(or messages\) to each other.   Each packet contains a collection of bytes, but each packet is separate and self-contained. 

**The socket type**

* STREAM \(TCP\)
* DATAGRAM \(UDP\)
* RAW \(Used for raw access to the wire\)

The data transmission determines your layer 4 protocol.

If your message is "fire and forget", you do not need error handling, or the whole communication is a small request with a small response \(e.g. DNS lookup\), you will use UDP.

If you are transferring a large amount of data, you require error handling and correction, or you don't know what to choose, use TCP.

In python, the socket module defines the constants as **SOCK\_STREAM** and **SOCK\_DGRAM** respectively. They handle layers 1-4 for you. If you need to control the lower layers, you will use RAW sockets.

---
<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/03-intro-to-sockets/bsd-socket-api/connections.md" > Continue to Next Topic </a>
