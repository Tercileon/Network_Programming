|[Table of Contacts](/00-Table-of-Contents.md)|
|---|

---

## sendall()

## Partial Reads/Writes

* Be aware that reading/writing to a socket may involve partial data transfer
* Send() returns actual bytes sent 
* recv() length is only a maximum limit

```
>>> len(data)
1000000
>>> s.send(data)
37722             <---------Sent partial data
>>>

>>> data = s.recv(10000)
>>> len(data)
6420              <---------Received less than max
>>>
```

* Be aware that for TCP, the data stream is continuous---no concept of records, etc.

```
# Client
...
s.send(data)
s.send(moredata)        <------
...                            |
                               |
# Sever                        |
...                            |
data = s.recv(maxsize)  <----- This recv() may return data from both of the sends cobined
...                            or less data thane even the first send
```

* A lot depends on OS buffers, network bandwidth, congestion, etc.

## Sending All Data

* To wait until all data is sent, use sendall()   
  `s.sendall(data)`  

* Blocks until all data is transmitted
* For most normal applications, this is what you should use
* Exception: You don't use this if networking is mixed in iwth other kinds of processing (e.g., screen updates, multitasking, etc.)

---

|[Next Topic](/03-intro-to-sockets/tcp-client-server/data-reassembly.md)|
|---|
