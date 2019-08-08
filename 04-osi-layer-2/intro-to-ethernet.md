<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" rel="Return to TOC"> Return to TOC </a>

# Intro to Ethernet

![](../.gitbook/assets/physical.PNG)

 Ethernet is a family of technologies used to connect LANs and WANs. It has used several different physical mediums over time from coaxial, to twisted pair, and now fiber.

The Ethernet protocol is the foundation of sending and receiving traffic and is the lowest level of network communication we will discuss in class.

The term Ethernet generally refers to a standard published in 1982 by Digital Equipment Corp., Intel Corp., and Xerox Corp. It is the predominant form of local area network technology used with TCP/IP today. It uses an access method called CSMA/CD, which stands for Carrier Sense, Multiple Access with Collision Detection. It operates at 10 Mbits/sec and uses 48-bit addresses.

A few years later the IEEE \(Institute of Electrical and Electronics Engineers\) 802 Committee published a sightly different set of standards. 802.3 covers an entire set of CSMA/CD networks....

In the TCP/IP world, the encapsulation of IP datagrams is defined in RFC 894 \[Hornig 1984\] for Ethernets and in RFC 1042 \[Postel and Reynolds 1988\] for IEEE 802 networks. The Host Requirements RFC requires that every Internet host connected to a 10 Mbits/sec Ethernet cable:

1. Must be able to send and receive packets using RFC 894 \(Ethernet\) encapsulation. 
2. Should be able to receive RFC 1042 \(IEEE 802\) packets intermixed with RFC 894 packets. 
3. May be able to send packets using RFC 1042 encapsulation. If the host can send both types of packets, the type of packet sent must be configurable and the configuration option must default to RFC 894 packets. 

---
<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/04-osi-layer-2/layer-1-devices.md" > Continue to Next Topic </a>
