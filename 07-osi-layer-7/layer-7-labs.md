<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" > Return to TOC </a>

# Lab 5-2

## Lab 5A:

Write a TCP Server that will generate a random number from 0 to 100. Then write a TCP Client that will receive an input from the user \(number 0 to 100\) and send the guess to the server. The server will then send back a message prompting the user to guess higher or lower. If the user guesses the correct number, have the server send back a success message and when the client receives the success message it will break the connection \(close the socket\).

## Lab 5B:

Create an IPv6 UDP chat server in Python using multicast to transmit to all clients.

Message strings should follow the following format:

**Username: TextGoes Here**

The receiver A should display recieved chats in the following format:

\[\(**IPv6Addr\)\]: The quick brown fox jumps over the lazy dogs**

\*\*Hints:

Ref:[http://man7.org/linux/man-pages/man7/ipv6.7.html](https://www.gitbook.com/book/cybertrainingusaf/iqt-network-programming-course/edit#)

Using the reference set the following socket options, with a level of socket.IPPROTO\_IPV6:

**Sender:**

•Set the multicast hops to 5

**Receiver:**

Set the socket's multicast group \(this is for the OS, it is \_NOT\_ IPv6 related\)

The group is a value obtained by combining the following:

* Packing the multicast IPv6 addr using socket.inet\_pton\(\)
* Packing a 32 bit unsigned integer with the value 0, using struct.pack\(\)

## 

---
<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/08-advanced-functionality/README.md" > Continue to Next Topic </a>

