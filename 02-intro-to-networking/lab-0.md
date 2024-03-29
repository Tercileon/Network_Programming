|[Table of Contacts](/00-Table-of-Contents.md)|
|---|

---

## Lab 0

In this lab you will be expected to be able to use Wireshark and Netcat for troubleshooting and debugging. Make sure you understand how to find Ethernet addresses and IP addresses. Startup Wireshark, have it listening to your Virtual Machine traffic, and verify connectivity between virtual machines before beginning the Labs.

* Use ifconfig to find your IP addresses.
* Become root.
* Use Netcat to connect your VMs together. 
* Use your filters in Wireshark and find the traffic being sent. 
* You can right-click on the IP of one of the VMs and select **Follow** the **TCP-Stream** to see the messages being sent \(the content of the packets transmitted\).

Practice filtering traffic by:

* IPv4/IPv6
* MAC Address
* port
* protocol
* A combination of the above

Familiarize yourself with the available options in Netcat.

Try to use Netcat:

* Instant message application
* To send a file
* As a port scanner
* Reverse Shell
* Banner Grab

---

|[Next Topic](/03-intro-to-sockets/README.md)|
|---|
