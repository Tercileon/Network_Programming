<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" > Return to TOC </a>

# TCP State

TCP sockets have numerous states. Many of these can be seen in the output of a properly timed netstat command.

## **Handshake states:**

* LISTEN: Awaiting a SYN
* SYN-Sent: A client has sent the SYN, and is awaiting the SYNACK
* SYN-RECIEVED: A server has received and a SYN, sent a SYNACK, and is awaiting the ACK

## **Data states:**

* **ESTABLISHED**: Normal data transmission occurring.
* **FIN-WAIT-1**: Client FIN sent, awaiting acknowledgement from Server. May still receive data.
* **FIN-WAIT-2**: Client FIN acknowledged by Server \(half closed\), awaiting Server FIN. May still receive data.
* **CLOSE\_WAIT**: Client FIN received and acknowledged by Server. Waiting for Server to send it's own FIN \(This is the server view of FIN-WAIT-1 & 2\).
* **LAST-ACK**: Server sends FIN. Awaiting Client to acknowledge it for teardown.
* **TIME-WAIT**: There is a "cooldown" period before the socket can be closed for good.
* **CLOSED**: No more connection.

**TIME-WAIT** is why you occasionally get errors that a port is in use when rapidly re-running code that creates network socket.

You can use socket options to solve this.

---

<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/06-osi-layer-4/rst-and-icmp.md" > Continue to Next Topic </a>
