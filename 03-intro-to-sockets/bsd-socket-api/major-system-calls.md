<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" rel="Return to TOC"> Return to TOC </a>

# Major System Calls

![](../../.gitbook/assets/systemcalls.PNG)

![](../../.gitbook/assets/calls.PNG)

A **CONNECTION** is a unique combination of:

* Client IP
* Client Port
* Server IP
* Server Port

If any one of these changes, it must be a different connection.

A connection is established between a TCP client and TCP server when the client uses **connect\(\)** to establish a connection to a TCP server listening. The result of that connection is the socket returned by **accept\(\)**.

---
<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/03-intro-to-sockets/bsd-socket-api/socket-basics.md" > Continue to Next Topic </a>
