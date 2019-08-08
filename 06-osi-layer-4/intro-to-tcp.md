<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" > Return to TOC </a>

# Intro to TCP

![TCP/IP Model](../.gitbook/assets/tcpip.PNG)

The Transmission Control Protocol is connection oriented, provides error checking, and reliability of communication.

Most protocols commonly used on the internet use TCP including: HTTP, SMTP, and SSH.

TCP connections open with a handshake, data is transmitted, and then the connection is closed with a tear down.

TCP provides reliable transfer via:

* Correctly ordering packets received in arbitrary order.
* Validating received packets were not corrupt.
* Re-requesting packets that were corrupt or not received at all.
* Flow and congestion control.
* Requires positive acknowledgement before next data transmission.

---

<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/06-osi-layer-4/layer-4-devices.md" > Continue to Next Topic </a>
