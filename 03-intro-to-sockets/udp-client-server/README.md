|[Table of Contacts](/00-Table-of-Contents.md)|
|---|

---

## UDP Client/Server

![](/assets/udp1.PNG)

**Datagram-based** 

* Connectionless
* unreliable \(no ordering of data\)
* can broadcast 
* Higher performance \(used in games, etc.\)

**Applications usually message-based** 

* No transport-layer retries 
* Applications handle \(or ignore\) errors 

**Processes identified by port number** 

**UDP Services live at specific ports** 

* Usually below 1024, requiring privilege

![](/assets/udp22.PNG)

![](/assets/udp33.PNG)

---

|[Next Topic](/03-intro-to-sockets/udp-client-server/order-of-operations.md)|
|---|
