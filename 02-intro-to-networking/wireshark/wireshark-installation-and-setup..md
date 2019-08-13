|[Table of Contacts](/00-Table-of-Contents.md)|
|---|

---

## Wireshark Installation and Setup.

In order to install the Wireshark GUI from repositories, simply type…

![](/assets/wireshark1.PNG)

…into a terminal. This will install both Qt and the CLI version of Wireshark. At this point, you can use Wireshark as root, but it is generally considered a bad practice. Therefore, we will set up permissions for regular users to capture on network interfaces \(see below about security implications\).

## Setting permissions

During installation, a system group called `wireshark` was created. Users in this group can capture network traffic. All you need to do is to add your user account into the group like this, substituting your username for _username_:

![](/assets/wireshark2.PNG)

Then log out, back in again, and you are ready to go!

---

|[Next Topic](/02-intro-to-networking/wireshark/analyzing-packets.md)|
|---|
