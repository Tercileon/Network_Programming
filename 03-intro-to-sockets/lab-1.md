<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" rel="Return to TOC"> Return to TOC </a>

# Lab 1-1

In this exercise, we experiment with setting up a network connection between two different Python interpreters.

On Windows, go to the "Start" menu and run the "Python \(command line\)" program. This should pop up a command window where you can directly interact with a Python interpreter.

![](../.gitbook/assets/python-cmd.PNG)

If you want to run it in Linux you can use the Terminal.

**\(a\) Waiting for a Connection**

In the new Python interpreter that you just opened, type the following commands to create a very simple network server:

> ```text
> >>>from socket import *
> >>>s = socket(AF_INET, SOCK_STREAM)
> >>>s.bind(("",15000))
> >>>s.listen(5)
> >>>c,a = s.accept()
> ```

These statements create a server that is now waiting for an incoming connection. The accept\(\) operation blocks forever until a connection arrives---so, you won't be able to do anything else until that happens.

**\(b\) Making a Connection**

Type the following statements to make a connection to your server program. Keep in mind, these statements are being typed into a _different_ Python interpreter than the one that's running in part \(a\).

> ```text
> >>>from socket import *
> >>>s = socket(AF_INET, SOCK_STREAM)
> >>>s.connect(("localhost",15000))
> >>>
> ```

Immediately after you issue the connect\(\) operation, your server program in part \(a\) should suddenly return back to the Python &gt;&gt;&gt; prompt. Type the following statements in the server to see the result.

> ```text
> >>>c
> <socket._socketobject object at 0x10028d910>
> >>>a
> ('127.0.0.1', 62793)
> >>>
> ```

The variable c returned by accept\(\) is a socket object that's connected to the remote client. The variable a is a tuple containing the IP address and port number of the remote client.

**\(c\) Sending Some Data**

In the interpreter \(the client\), type the following statement to send a "Hello World" message to the server:

> ```text
> >>>s.send("Hello World")
> 11
> >>>
> ```

In the server, type the following to receive the message:

> ```text
> >>>data = c.recv(1024)
> >>>data
> 'Hello World'
> >>>
> ```

Have the server send a message back to the client:

> ```text
> >>>c.send("Hello Yourself")
> 14
> >>>
> ```

Have the client receive the server's response. Type:

> ```text
> >>>resp = s.recv(1024)
> >>>resp
> 'Hello Yourself'
> >>>
> ```

Observe that you are sending data back and forth between the two Python interpreters. Try more send\(\) and recv\(\) operations if you want to send more data.

**\(d\) Closing the Connection**

In the client, issue a recv\(\) operation to wait for more data. This should block since the server hasn't actually sent any additional data yet.

> ```text
> >>>s.recv(1024)
> ```

In the server, send a goodbye message and close the socket.

> ```text
> >>>c.send("Goodbye")
> 7
> >>>c.close()
> >>>
> ```

When the send\(\) operation completes, the client should display the 'Goodbye' message. For example:

> ```text
> >>>s.recv(1024)   (from before)
> 'Goodbye'
> >>>
> ```

Try reading more data and see what happens:

> ```text
> >>>s.recv(1024)
> ''
> >>>
> ```

You'll notice that the recv\(\) operation returns with an empty string. This is the indication that the server has closed the connection and that there is no more data. There is nothing more than the client can do with the socket at this point.

**\(e\) Listening for a new connection**

After the server has closed the client connection, it typically goes back to listening by issuing a new accept\(\) command. Type this in the server:

> ```text
> >>>c,a = s.accept()
> ```

Once again, the server now waits until a new connection arrives.

**\(f\) Connecting with a Browser**

Try connecting to your server program using your internet browser. Type this link into the navigation bar:

[http://localhost:15000/index.html](http://localhost:15000/index.html)

In your server program, you should see that the accept\(\) operation has returned. Try reading the browser request and print it out.

> ```text
> >>>request = c.recv(8192)
> >>>print request
> ... look at the result ...
> >>>
> ```

Send an HTML greeting back to the browser:

> ```text
> >>>c.send("HTTP/1.1 200 OK\r\n")
> >>>c.send("Content-type: text/html\r\n")
> >>>c.send("\r\n")
> >>>c.send("<h1>Hello World</h1>")
> >>>c.close()
> >>>
> ```

Congratulations! You have now made an extremely simple web server.

---
<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/03-intro-to-sockets/lab-1-2.md" > Continue to Lab 1-2 </a>
