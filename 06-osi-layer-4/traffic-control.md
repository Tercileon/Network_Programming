<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" > Return to TOC </a>

# Traffic Control

Window scaling is determined during the handshake and it determines the maximum data to be received before being ACKed.

Flow control in TCP is accomplished using a sliding window. Receivers specify the amount of data that they are willing to receive, and the sender will only send that much before waiting for an ACK. If the window is 0, transmission stops for a timeout to allow the receiver to ACK with a new window.

Congestion is controlled by the TCP stack using timers and various algorithms to estimate round trip time, and will speed up or slow down data based upon that information.

In depth analysis of these are out of the scope of this class.

---

<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/06-osi-layer-4/udp.md" > Continue to Next Topic </a>
