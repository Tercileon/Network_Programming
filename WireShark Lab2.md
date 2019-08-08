
## Examine

Find these features, as shown below:

Packet List in the top pane, showing one line per packet. Notice the TCP handshake performed by packets 1, 3, and 4, outlined in red in the image below.

Packet Details in the middle pane, showing the first four TCP layers. Notice MAC addresses at layer 2, IP addresses at layer 3, and TCP port numbers at layer 4, outlined in green in the image below.

Packet Bytes in the bottom pane, showing raw data in hexadecimal and ASCII form, outlined in red in the blue below. 

![123p6wire1](https://user-images.githubusercontent.com/47218652/60917438-960f8f00-a256-11e9-9daf-48a044836c2f.png)

## Finding an FTP Password

FTP is a very unsafe protocol, because it sends passwords over the network without encryption. To demonstrate that, we'll steal a password.

In Wireshark, at the top, in the "Apply a display filter" box, type ftp and press the Enter key.

Wireshark filters the packets, showing only the packets using File Transfer Protocol. On the right side, you can see the login process for a user named "john". Find John's password, which is covered by a gray box in the image below. 

![123p6wire2](https://user-images.githubusercontent.com/47218652/60917439-960f8f00-a256-11e9-97b1-c4975bb0f9de.png)

### Take a SCREENSHOT OF YOUR FINDINGS 

## Finding an HTTP Password

HTTP also sends passwords over the network without encryption. To demonstrate that, we'll steal a password.

Download this file and double-click it to open it in Wireshark:

httplogin.pcapng

In Wireshark, at the top, in the "Apply a display filter" box, type http and press the Enter key.

Wireshark filters the packets, showing only the packets using HTTP. In the Packet List, in the "Info" column, find the first POST request, as shown below, and click it.

In the Packet Details, expand the "Hypertext Transfer Protocol" container. The username of "Isaac" and password of "Flapper" are visibie, as outlined in red in the image below. 

![123p6wire3](https://user-images.githubusercontent.com/47218652/60917440-960f8f00-a256-11e9-8308-8c3706d5023a.png)

## Following a TCP Stream

In the Packet List, in the "Info" column, right-click the first POST request, click Follow, and click "TCP Stream", as shown below, 

<img width="609" alt="123p6wire4" src="https://user-images.githubusercontent.com/47218652/60917441-96a82580-a256-11e9-81e5-2203c6bc833d.png">

 The conversation is shown, with the client's transmission in red, and the server's response in blue, as shown below.

The TCP Stream is often very helpful, but not in this case, because the reply is zipped. 

<img width="380" alt="123p6wire5" src="https://user-images.githubusercontent.com/47218652/60917442-96a82580-a256-11e9-8ba9-9e8c5a74fe05.png">

## Restoring the Packet Filter to "http"

Close the "Follow TCP Stream" box.

In Wireshark, at the top, in the "Apply a display filter" box, on the right side, click the X to clear the filter.

In the "Apply a display filter" box, type http and press the Enter key.

All the "http" packets appear, as shown below. 

## Viewing the HTTP Reply

In the Packet List, in the "Info" column, click the packet following the first POST request, which is labelled "HTTP/1.1 200 OK", as shown below.

In the Packet Details, expand the "Line-based test data" container. The server's reply is now readable, saying "Login Denied!", as outlined in red in the image below. 

![123p6wire6](https://user-images.githubusercontent.com/47218652/60917443-96a82580-a256-11e9-8bb5-c1ca758d6dce.png)

## Finding Isaac's Password

Isaac made several attempts to log in before finally entering the correct password. 

## Recording Your Success

Find the password that worked and submit it to the Instructor. 

## HTTP Basic Authentication

HTTP Basic authentication obfuscates passwords with Base64 encoding before transmitting them, which is not much better than sending them in cleartext, because Wireshark automatically decodes them.

Download this file and double-click it to open it in Wireshark:

BasicLogin.pcapng

A user named WALDO logged in. Find Waldo's password and submit it. 

## Recording Your Success

Submit it to the Instructor
