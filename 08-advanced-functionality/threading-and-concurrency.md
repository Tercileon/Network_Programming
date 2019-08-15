|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## Threading and Concurrency

### Thread Objects

The simplest way to use a Thread is to instantiate it with a target function and call start\(\) to let it begin working.

```text
import threading

def worker():
    """thread worker function"""
    print 'Worker'
    return

threads = []
for i in range(5):
    t = threading.Thread(target=worker)
    threads.append(t)
    t.start()
```

The output is five lines with "Worker" on each:

```text
$ python threading_simple.py

Worker
Worker
Worker
Worker
Worker
```

It is useful to be able to spawn a thread and pass it arguments to tell it what work to do. This example passes a number, which the thread then prints.

```text
import threading

def worker(num):
    """thread worker function"""
    print 'Worker: %s' % num
    return

threads = []
for i in range(5):
    t = threading.Thread(target=worker, args=(i,))
    threads.append(t)
    t.start()
```

The integer argument is now included in the message printed by each thread:

```text
    $ python -u threading_simpleargs.py

Worker: 0
Worker: 1
Worker: 2
Worker: 3
Worker: 4
```

![](../.gitbook/assets/conc1.PNG)

![](../.gitbook/assets/conc2.PNG)

![](../.gitbook/assets/conc3.PNG)

#### To manage multiple clients

* Server must always be ready to accept new connections
* Must allow each client to operate independently \(each may be performing different tasks on the server\) 

![](../.gitbook/assets/conc4.PNG)

### Example:

In order to show an example of threading on a server to handle concurrent connections, we're going to use this example of an echo server that sends an echo reply of the incoming message back to the client.

```text
import socket
import sys

HOST = ''   # Symbolic name meaning all available interfaces
PORT = 5000 # Arbitrary non-privileged port

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
print 'Socket created'

try:
    s.bind((HOST, PORT))
except socket.error , msg:
    print 'Bind failed. Error Code : ' + str(msg[0]) + ' Message ' + msg[1]
    sys.exit()

print 'Socket bind complete'

s.listen(10)
print 'Socket now listening'

#accept will run in a loop and the server will stay active
while 1:
    #wait to accept a connection - blocking call
    conn, addr = s.accept()
    print 'Connected with ' + addr[0] + ':' + str(addr[1])

    data = conn.recv(1024)
    reply = 'OK...' + data
    if not data: 
        break

    conn.sendall(reply) #sendall blocks until all of the transmission is sent

conn.close()
s.close()
```

Now run the server program in 1 terminal , and open 3 other terminals.  
From each of the 3 terminals run netcat and connect to the server port.

Each of the netcat terminals should show:

```text
$ nc localhost 5000
happy
OK .. happy
Ncat broken pipe
```

And the server terminal should show:

```text
$ python server.py
Socket created
Socket bind complete
Socket now listening
Connected with 127.0.0.1:60225
Connected with 127.0.0.1:60237
Connected with 127.0.0.1:60239
```

Each terminal is able to connect to the server.  However, the server cannot communicate with all three and will only respond to one message. So we need to create separate handlers to manage each connection.

#### Handling Connections

One way to achieve this is using threads. The main server program accepts a connection and creates a new thread to handle communication for the connection, and then the server goes back to accept more connections.

```text
import socket
import sys
from thread import *

HOST = ''   # Symbolic name meaning all available interfaces
PORT = 8888 # Arbitrary non-privileged port

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
print 'Socket created'

#Bind socket to local host and port
try:
    s.bind((HOST, PORT))
except socket.error , msg:
    print 'Bind failed. Error Code : ' + str(msg[0]) + ' Message ' + msg[1]
    sys.exit()

print 'Socket bind complete'

#Start listening on socket
s.listen(10)
print 'Socket now listening'

#Function for handling connections. This will be used to create threads
def clientthread(conn):
    #Sending message to connected client
    conn.send('Welcome to the server. Type something and hit enter\n') #send only takes string

    #infinite loop so that function do not terminate and thread do not end.
    while True:

        #Receiving from client
        data = conn.recv(1024)
        reply = 'OK...' + data
        if not data: 
            break

        conn.sendall(reply)

    #came out of loop
    conn.close()

#now keep talking with the client
while 1:
    #wait to accept a connection - blocking call
    conn, addr = s.accept()
    print 'Connected with ' + addr[0] + ':' + str(addr[1])

    #start new thread takes 1st argument as a function name to be run, second is the tuple of arguments to the function.
    start_new_thread(clientthread ,(conn,))

s.close()
```

Run the above server and open 3 terminals like before. Now the server will create a thread for each client connecting to it. and be able to continuously communicate with each client.

#### References:

`thread.start_new_thread`\(_function_, _args_\[, _kwargs_\]\)

Start a new thread and return its identifier. The thread executes the function _function_ with the argument list _args_ \(which must be a tuple\). The optional _kwargs_ argument specifies a dictionary of keyword arguments. When the function returns, the thread silently exits. When the function terminates with an unhandled exception, a stack trace is printed and then the thread exits \(but other threads continue to run\).

[https://docs.python.org/2/library/thread.html](https://docs.python.org/2/library/thread.html)

---

**End of Networkprogramming**

---

|<a href="https://github.com/Tercileon/A-La-Cart" > Return to Cyber A-La-Carte </a>|
|---|
