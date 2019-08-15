<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" > Return to TOC </a>

## DHCP

###  Dynamic Host Configuration Protocol \(DHCP\):

A client/server protocol that automatically provides an Internet Protocol \(IP\) host with its IP address and other related configuration information such as the subnet mask and default gateway. RFCs 2131 and 2132 define DHCP as an Internet Engineering Task Force \(IETF\) standard based on Bootstrap Protocol \(BOOTP\), a protocol with which DHCP shares many implementation details. DHCP allows hosts to obtain required TCP/IP configuration information from a DHCP server.

![](/assets/image_10.png)

Every device on a TCP/IP-based network must have a unique IP address to access the network and its resources. Without DHCP, IP addresses for new computers or computers that are moved from one subnet to another, must be configured manually; IP addresses for computers that are removed from the network must be manually reclaimed.

With DHCP, this entire process is automated and managed centrally. The DHCP server maintains a pool of IP addresses and leases an address to any DHCP-enabled client when it starts up on the network. Because the IP addresses are dynamic \(leased\) rather than static \(permanently assigned\), addresses no longer in use are automatically returned to the pool for reallocation.

#### DHCP provides the following benefits.

* **Reliable IP address configuration**. DHCP minimizes configuration errors caused by manual IP address configuration, such as typographical errors, or address conflicts caused by the assignment of an IP address to more than one computer at the same time.
* **Reduced network administration**. DHCP includes the following features to reduce network administration:
  * Centralized and automated TCP/IP configuration.
  * The ability to define TCP/IP configurations from a central location.
  * The ability to assign a full range of additional TCP/IP configuration values by means of DHCP options.
  * The efficient handling of IP address changes for clients that must be updated frequently, such as those for portable devices that move to different locations on a wireless network.
  * The forwarding of initial DHCP messages by using a DHCP relay agent, which eliminates the need for a DHCP server on every subnet.

---

|[Next Topic](/07-osi-layer-7/review.md)|
|---|
