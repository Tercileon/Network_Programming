<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" > Return to TOC </a>

# Network Byte Order

Network byte order is most-significant byte first.

Byte ordering at a host may differ.

`socket.ntohl(x)`

Convert 32-bit positive integers from network to host byte order. On machines where the host byte order is the same as network byte order, this is a no-op; otherwise, it performs a 4-byte swap operation.

`socket.ntohs(x)`

Convert 16-bit positive integers from network to host byte order. On machines where the host byte order is the same as network byte order, this is a no-op; otherwise, it performs a 2-byte swap operation.

`socket.htonl(x)`

Convert 32-bit positive integers from host to network byte order. On machines where the host byte order is the same as network byte order, this is a no-op; otherwise, it performs a 4-byte swap operation.

`socket.htons(x)`

Convert 16-bit positive integers from host to network byte order. On machines where the host byte order is the same as network byte order, this is a no-op; otherwise, it performs a 2-byte swap operation.

`socket.inet_aton(ip_string)`

Convert an IPv4 address from dotted-quad string format \(for example, ‘123.45.67.89’\) to 32-bit packed binary format, as a string four characters in length. This is useful when conversing with a program that uses the standard C library and needs objects of type`structin_addr`, which is the C type for the 32-bit packed binary this function returns.

* [`inet_aton()`](https://docs.python.org/2/library/socket.html#socket.inet_aton)also accepts strings with less than three dots; see the Unix manual page\_inet\(3\)\_for details.

If the IPv4 address string passed to this function is invalid,[`socket.error`](https://docs.python.org/2/library/socket.html#socket.error)will be raised. Note that exactly what is valid depends on the underlying C implementation of`inet_aton()`

* [`inet_aton()`](https://docs.python.org/2/library/socket.html#socket.inet_aton)does not support IPv6, and[`inet_pton()`](https://docs.python.org/2/library/socket.html#socket.inet_pton)should be used instead for IPv4/v6 dual stack support.

`socket.inet_ntoas(packed_ip)`

Convert a 32-bit packed IPv4 address \(a string four characters in length\) to its standard dotted-quad string representation \(for example, ‘123.45.67.89’\). This is useful when conversing with a program that uses the standard C library and needs objects of type`structin_addr`, which is the C type for the 32-bit packed binary data this function takes as an argument.

If the string passed to this function is not exactly 4 bytes in length,[`socket.error`](https://docs.python.org/2/library/socket.html#socket.error)will be raised.[`inet_ntoa()`](https://docs.python.org/2/library/socket.html#socket.inet_ntoa)does not support IPv6, and[`inet_ntop()`](https://docs.python.org/2/library/socket.html#socket.inet_ntop)should be used instead for IPv4/v6 dual stack support.

`socket.inet_pton(address_family, ip_string)`

Convert an IP address from its family-specific string format to a packed, binary format.[`inet_pton()`](https://docs.python.org/2/library/socket.html#socket.inet_pton)is useful when a library or network protocol calls for an object of type`structin_addr`\(similar to[`inet_aton()`](https://docs.python.org/2/library/socket.html#socket.inet_aton)\) or`structin6_addr`

Supported values for\_address\_family\_are currently[`AF_INET`](https://docs.python.org/2/library/socket.html#socket.AF_INET)and[`AF_INET6`](https://docs.python.org/2/library/socket.html#socket.AF_INET6). If the IP address string\_ip\_string\_is invalid,[`socket.error`](https://docs.python.org/2/library/socket.html#socket.error)will be raised. Note that exactly what is valid depends on both the value of\_address\_family\_and the underlying implementation of`inet_pton()`

Availability: Unix \(maybe not all platforms\).

`socket.inet_ntop(address_family, packed_ip)`

Convert a packed IP address \(a string of some number of characters\) to its standard, family-specific string representation \(for example,`'7.10.0.5'`or`'5aef:2b::8'`\)[`inet_ntop()`](https://docs.python.org/2/library/socket.html#socket.inet_ntop)is useful when a library or network protocol returns an object of type`structin_addr`\(similar to[`inet_ntoa()`](https://docs.python.org/2/library/socket.html#socket.inet_ntoa)\) or`structin6_addr`

Supported values for\_address\_family\_are currently[`AF_INET`](https://docs.python.org/2/library/socket.html#socket.AF_INET)and[`AF_INET6`](https://docs.python.org/2/library/socket.html#socket.AF_INET6). If the string\_packed\_ip\_is not the correct length for the specified address family,[`ValueError`](https://docs.python.org/2/library/exceptions.html#exceptions.ValueError)will be raised. A[`socket.error`](https://docs.python.org/2/library/socket.html#socket.error)is raised for errors from the call to[`inet_ntop()`](https://docs.python.org/2/library/socket.html#socket.inet_ntop)

Availability: Unix \(maybe not all platforms\).

---

<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/08-advanced-functionality/socket-timeout.md" > Continue to Next Topic </a>
