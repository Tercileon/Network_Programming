|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

# Lab 3-2

## Lab 3A

Using the struct package from the python library, pack the values \(1, 2, -3, -4\) as the following data types \(unsigned short, unsigned int, signed short, signed int\)

1 as an unsigned short

2 as an unsigned int

-3 as a signed short

-4 as a signed int

Write a TCP client that packs those values, sends the packed string to a server.

Write a TCP server that receives the string, unpacks it using little endian and prints it, then unpacks it again using big endian and prints it.

## Lab 3B

Write a UDP receiver that receives a string, and orders the words from longest to shortest in a new string.

That new string should be sent to the remote port+1.

\(i.e. the source port of message from the SENDER's POV\)

Write a UDP sender that sends the initial string, and receives the response from the receiver above \(you can use multiple receivers or combine them\).

Hint: The second step is intentionally ambiguous on how to proceed. There are multiple solutions.

## Bonus:  

#### Create a port scanner. Code it in Python, C, or Raw Sockets. Use IPv4 or IPv6, TCP and/or UDP.

---

|[Next Topic](/06-osi-layer-4/README.md)|
|---|
