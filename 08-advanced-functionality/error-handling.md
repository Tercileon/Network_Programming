<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" > Return to TOC </a>

# Error Handling

**If any of the socket functions fail then python throws an exception called socket.error which must be caught.**

```text
#handling errors in python socket programs

import socket  #for sockets
import sys  #for exit

try:
    #create an AF_INET, STREAM socket (TCP)
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
except socket.error, msg:
    print 'Failed to create socket. Error code: ' + str(msg[0]) +' , Error message : ' + msg[1]
sys.exit();
print 'Socket Created'
```

All errors raise exceptions. The normal exceptions for invalid argument types and out-of-memory conditions can be raised; errors related to socket or address semantics raise the error[`socket.error`](https://docs.python.org/2/library/socket.html?highlight=pton#socket.error).

Non-blocking mode is supported through[`setblocking()`](https://docs.python.org/2/library/socket.html?highlight=pton#socket.socket.setblocking). A generalization of this based on timeouts is supported through[`settimeout()`](https://docs.python.org/2/library/socket.html?highlight=pton#socket.socket.settimeout).

The module[`socket`](https://docs.python.org/2/library/socket.html?highlight=pton#module-socket)exports the following constants and functions:

_exception_ `socket.error`

This exception is raised for socket-related errors. The accompanying value is either a string telling what went wrong or a pair`(errno,string)`representing an error returned by a system call, similar to the value accompanying[`os.error`](https://docs.python.org/2/library/os.html#os.error). See the module[`errno`](https://docs.python.org/2/library/errno.html#module-errno), which contains names for the error codes defined by the underlying operating system.

Changed in version 2.6:[`socket.error`](https://docs.python.org/2/library/socket.html?highlight=pton#socket.error)is now a child class of[`IOError`](https://docs.python.org/2/library/exceptions.html#exceptions.IOError).

_exception_ `socket.herror`

This exception is raised for address-related errors, i.e. for functions that use\_h\_errno\_in the C API, including[`gethostbyname_ex()`](https://docs.python.org/2/library/socket.html?highlight=pton#socket.gethostbyname_ex)and[`gethostbyaddr()`](https://docs.python.org/2/library/socket.html?highlight=pton#socket.gethostbyaddr).

The accompanying value is a pair`(h_errno,string)`representing an error returned by a library call._string\_represents the description of\_h\_errno_, as returned by the`hstrerror()`C function.

_exception_`socket.gaierror`

This exception is raised for address-related errors, for[`getaddrinfo()`](https://docs.python.org/2/library/socket.html?highlight=pton#socket.getaddrinfo)and[`getnameinfo()`](https://docs.python.org/2/library/socket.html?highlight=pton#socket.getnameinfo). The accompanying value is a pair`(error,string)`representing an error returned by a library call._string\_represents the description of\_error_, as returned by the`gai_strerror()`C function. The  _error\_value will match one of the\`EAI_\*\`constants defined in this module.

_exception_`socket.timeout`

This exception is raised when a timeout occurs on a socket which has had timeouts enabled via a prior call to`settimeout()`. The accompanying value is a string whose value is currently always “timed out”.

---

<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/08-advanced-functionality/json-module.md" > Continue to Next Topic </a>
