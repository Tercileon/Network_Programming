<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" rel="Return to TOC"> Return to TOC </a>

# Data Encapsulation and The TCP/IP Model

![](../.gitbook/assets/encapsulation.PNG)

**Data Encapsulation:**  The process of taking data from one protocol and translating it into another protocol, so the data can continue across the network.   During encapsulation, each layer builds a protocol data unit \(PDU\) by adding a header \(and sometimes a footer\) containing control information to the PDU from the layer above.

![OSI vs TCP/IP](../.gitbook/assets/image%20%281%29.png)

* **Layer 4\) Application:** Telnet, SSH, FTP, POP3, SMTP, HTTP, etc...
* **Layer 3\) Transport:** TCP and UDP
* **Layer 2\)** **Internet:**  IP Addressing and Routing
* **Layer 1\)** **Network Access Layer:**  Ethernet, Wi-Fi, "Hardware", etc...

---
<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/04-osi-layer-2/intro-to-ethernet.md" > Continue to Next Topic </a>
