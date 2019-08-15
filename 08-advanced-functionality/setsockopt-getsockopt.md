|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## setsockopt\(\)/getsockopt\(\)

Using socket options gives you some advanced options for sockets to do interesting things.

Options have a LEVEL, OPTION NAME, and a VALUE.

* LEVEL can be the entire socket \(socket.SOL\_SOCKET\) or a specific protocol \(socket.IPPROTO\_IPV6\).
* The LEVEL specified determines what OPTION NAMEs are available to be set.
* VALUES are assigned to the specified OPTION NAME.

Unfortunately, options are scattered all over the place in documentation. Man pages are currently the best source or for a grouping of common ones, see the refs.

#### `socket.setsockopt`\(_level_,  _optname_,  _value_\)

Set the value of the given socket option \(see the Unix manual page_setsockopt\(2\)_\). The needed symbolic constants are defined in the[`socket`](https://docs.python.org/2/library/socket.html#module-socket)module \(`SO_*`etc.\). The value can be an integer or a string representing a buffer. In the latter case it is up to the caller to ensure that the string contains the proper bits \(see the optional built-in module[`struct`](https://docs.python.org/2/library/struct.html#module-struct)for a way to encode C structures as strings\).

#### `socket.getsockopt`\(_level_,  _optname_\[,  _buflen_\]\)

Return the value of the given socket option \(see the Unix man page_getsockopt\(2\)_\). The needed symbolic constants \(`SO_*`etc.\) are defined in this module. If\_buflen\_is absent, an integer option is assumed and its integer value is returned by the function. If\_buflen\_is present, it specifies the maximum length of the buffer used to receive the option in, and this buffer is returned as a string. It is up to the caller to decode the contents of the buffer \(see the optional built-in module[`struct`](https://docs.python.org/2/library/struct.html#module-struct)for a way to decode C structures encoded as strings\).

The default socket buffer size may not be suitable in many circumstances. In such circumstances, you can change the default socket buffer size to a more suitable value.

### How to do it...

Let us manipulate the default socket buffer size using a socket object's`setsockopt()`method.

First, define two constants:`SEND_BUF_SIZE`/`RECV_BUF_SIZE`and then wrap a socket instance's call to the`setsockopt()`method in a function. It is also a good idea to check the value of the buffer size before modifying it. Note that we need to set up the send and receive buffer size separately.

Listing 1.8 shows how to modify socket send/receive buffer sizes as follows:

```text
import socket

SEND_BUF_SIZE = 4096
RECV_BUF_SIZE = 4096

def modify_buff_size():
    sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM )

    # Get the size of the socket's send buffer
    bufsize = sock.getsockopt(socket.SOL_SOCKET, socket.SO_SNDBUF)
    print "Buffer size [Before]:%d" %bufsize

    sock.setsockopt(socket.SOL_TCP, socket.TCP_NODELAY, 1)
    sock.setsockopt(
            socket.SOL_SOCKET,
            socket.SO_SNDBUF,
            SEND_BUF_SIZE)
    sock.setsockopt(
            socket.SOL_SOCKET,
            socket.SO_RCVBUF,
            RECV_BUF_SIZE)
    bufsize = sock.getsockopt(socket.SOL_SOCKET, socket.SO_SNDBUF)
    print "Buffer size [After]:%d" %bufsize

if __name__ == '__main__':
    modify_buff_size()
```

If you run the preceding script, it will show the changes in the socket's buffer size. The following output may be different on your machine depending on your operating system's local settings:

```text
$ python 1_8_modify_buff_size.py 
Buffer size [Before]:16384
Buffer size [After]:8192
```

### How it works...

You can call the`getsockopt()`and`setsockopt()`methods on a socket object to retrieve and modify the socket object's properties respectively. The`setsockopt()`method takes three arguments:`level`,`optname`, and`value`. Here,`optname`takes the option name and`value`is thecorrespondingvalue of that option. For the first argument, the needed symbolic constants can be found in the socket module \(`SO_*etc.`\).

#### See Also:

[http://man7.org/linux/man-pages/man2/setsockopt.2.html](http://man7.org/linux/man-pages/man2/setsockopt.2.html)

[https://linux.die.net/man/2/getsockopt](https://linux.die.net/man/2/getsockopt)

---

|[Next Topic](/08-advanced-functionality/network-byte-order.md)|
|---|
