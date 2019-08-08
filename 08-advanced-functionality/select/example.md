<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" > Continue to Next Topic </a>

# Example

```text
import select, socket, sys, Queue
server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server.setblocking(0)
server.bind(('localhost', 50000))
server.listen(5)
inputs = [server]
outputs = []
message_queues = {}

while inputs:
    readable, writable, exceptional = select.select(inputs, outputs, inputs)
    for s in readable:
        if s is server:
            connection, client_address = s.accept()
            connection.setblocking(0)
            inputs.append(connection)
            message_queues[connection] = Queue.Queue()
        else:
            data = s.recv(1024)
            if data:
                message_queues[s].put(data)
                if s not in outputs:
                    outputs.append(s)
            else:
                if s in outputs:
                    outputs.remove(s)
                inputs.remove(s)
                s.close()
                del message_queues[s]

    for s in writable:
        try:
            next_msg = message_queues[s].get_nowait()
        except Queue.Empty:
            outputs.remove(s)
        else:
            s.send(next_msg)

    for s in exceptional:
        inputs.remove(s)
        if s in outputs:
            outputs.remove(s)
        s.close()
        del message_queues[s]
```

Creating server socket looks the same except for one line:`server.setblocking(0)` This is done to make the socket nonblocking. This server is more advanced since it can serve more than one client. The main point is in`selecting`sockets:

```text
readable, writable, exceptional = select.select(inputs, outputs, inputs)
```

Here we call`select.select`to ask the OS to check given sockets whether they are ready to write, read, or if there is some exception respectively. That is why it passes three lists of sockets to specify which socket is expected to be writable, readable, and which should be checked for errors. This call will block the program \(unless a timeout argument is passed\) until some of the passed sockets are ready. In this moment, the call will return three lists with sockets for specified operations.

Then it sequentially iterates over those lists and, if there are sockets in them, it performs corresponding operations. When there is the server socket in`inputs`, it means that a new client has arrived. Therefore, it calls`accept()`, adds a returned socket to`inputs`and adds a`Queue`for incoming messages which will be sent back. If there is another socket in inputs, then some messages have arrived and ready to be read so it reads them and places them into the corresponding queue.

For writable sockets, it gets pending messages \(if any\) and writes them to the socket. If there is any error in the socket, it removes the socket from the lists.

This is how sockets work at a lower level. However, in most cases, there is no need to implement the logic at such a low level. It is recommended to use some higher level abstractions such as Twisted, Tornado, or ZeroMQ, depending on the situation.

---

<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/08-advanced-functionality/socketserver/README.md" > Continue to Next Topic </a>
