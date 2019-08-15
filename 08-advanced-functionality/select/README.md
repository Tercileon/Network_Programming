|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## select\(\)

* Select\(\) is a potential solution for when you want to open multiple sockets for communication, but don't want your receive/send functions to block and hold up your program.
* Select is a Linux function call that operates on file descriptors. In Linux specifically, everything is a file. This means at it's core in Linux, a network socket is a file descriptor.
* Since it's a sys call, it works in C, Python, and any other language you can make syscalls from \(in Linux anyway\). Under the hood it is a wrapper for poll\(\).

### select.select\(rlist, wlist, xlist\[, timeout\]\)

This is a straightforward interface to the Unix select system call. The first three arguments are sequences of ‘waitable objects’: either integers representing file descriptors or objects with a parameterless method named fileno\(\) returning such an integer:

* _rlist_: wait until ready for reading
* _wlist_: wait until ready for writing
* _xlist_: wait for an “exceptional condition” \(see the manual page for what your system considers such a condition\)

Empty sequences are allowed, but acceptance of three empty sequences is platform-dependent. \(It is known to work on Unix but not on Windows.\) The optional _timeout_ argument specifies a time-out as a floating point number in seconds. When the _timeout_ argument is omitted the function blocks until at least one file descriptor is ready. A time-out value of zero specifies a poll and never blocks.

The return value is a triple of lists of objects that are ready: subsets of the first three arguments. When the time-out is reached without a file descriptor becoming ready, three empty lists are returned.

Among the acceptable object types in the sequences are Python file objects \(e.g. sys.stdin, or objects returned by [open\(\)](https://docs.python.org/3.0/library/functions.html#open) or os.popen\(\)\), socket objects returned by [socket.socket\(\)](https://docs.python.org/3.0/library/socket.html#socket.socket). You may also define a _wrapper_ class yourself, as long as it has an appropriate fileno\(\) method \(that really returns a file descriptor, not just a random integer\).

You pass`select`three lists: the first contains all sockets that you might want to try reading; the second all the sockets you might want to try writing to, and the last \(normally left empty\) those that you want to check for errors. You should note that a socket can go into more than one list. The`select`call is blocking, but you can give it a timeout. This is generally a sensible thing to do - give it a nice long timeout \(say a minute\) unless you have good reason to do otherwise.

In return, you will get three lists. They contain the sockets that are actually readable, writable and in error. Each of these lists is a subset \(possibly empty\) of the corresponding list you passed in.

If a socket is in the output readable list, you can be as-close-to-certain-as-we-ever-get-in-this-business that a`recv`on that socket will return_something_. Same idea for the writable list. You’ll be able to send_something_. Maybe not all you want to, but\_something\_is better than nothing. \(Actually, any reasonably healthy socket will return as writable - it just means outbound network buffer space is available.\)

If you have a “server” socket, put it in the potential\_readers list. If it comes out in the readable list, your`accept`will \(almost certainly\) work. If you have created a new socket to`connect`to someone else, put it in the potential\_writers list. If it shows up in the writable list, you have a decent chance that it has connected.

One very nasty problem with`select`: if somewhere in those input lists of sockets is one which has died a nasty death, the`select`will fail. You then need to loop through every single damn socket in all those lists and do a`select([sock],[],[],0)`until you find the bad one. That timeout of 0 means it won’t take long, but it’s ugly.

### Socket Setup

We need to import select, and set our sockets to be non-blocking.

```text
import select
    ...
    p1 = socket.socket(socket.AF_INET, socket.SOCK_STREAM) 
    p1.setblocking(0)
    p1.bind( ('', 2000) )
    p1.listen(1)
    p2 = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    p2.setblocking(0)
    p2.bind( ('', p2port) ) 
    p2.listen(1)
```

### Setting Up a Call

Select\(\) takes 3 parameters, each is a list of file descriptors.

The first parameter is for reads.

The second parameter is for writes.

The third parameter to see if there is any fds that threw an exception.

FDs can be in multiple lists.

#### `# Sockets to which we expect to read`

#### `inputs = [ p1, p2 ]`

#### `# Sockets to which we expect to write`

#### `outputs = [ ]`

#### `readable, writable, exceptional =select.select(inputs, outputs, inputs)`

### Using It

You do NOT need to use all return values in the for-loops below. If you only care about reading, then omit the remaining two loops.

The returned lists may also be handled in any order. If you prioritize writes, handle that list first.

Remember that the parameters and return values are all Python lists. There is NO guarantee of order of sockets within those lists.

```text
socklist = [mysock1: ‘host1’, mysock2: ‘host1:8080’, mysock3: ‘host2-description’}

    while True:
        readable, writable, exceptional = select.select(inputs, outputs, inputs)    
        for s in readable:
            # compare s to your socket list to find out which one it is
            # read incoming data and handle it
        for s in writeable:
            # compare s to your socket list to find out which one it is
            # identify data that goes to that socket, and write it
        for s in exceptional:
            # compare s to your socket list to find out which one it is
            # handle the exception
            # You may have internal states to keep track of. Update them now 
                (e.g. is the user logged in? How far along in a buffer are you)
```

---

|[Next Topic](/08-advanced-functionality/select/example.md)|
|---|
