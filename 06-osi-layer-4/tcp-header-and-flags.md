|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## TCP Header and Flags

![TCP Header](/assets/mjb-tcp-header-800x564.png)

**Source Port** – sending port

**Destination Port** – Receiving port

**Sequence Number** – Initially random. Each new transmission adds the size of the data

**Acknowledgment Number** – The next byte expected to be received.

**Data offset** - Size of TCP header in 32bit words

**Reserved** – 0's

**Flags** – Bit mask of all TCP flags

**Window size** – Max number of bytes receiver can handle

**Checksum** – Checksum of header and data

**Urgent Pointer** – Only valid if URG flag set

**Options** – Allows for expanded uses

![](/assets/tcphead.PNG)

### TCP uses a bit field to represent flags.

**NS - Nonce Sum**, used to counter an old method for an attacker attempting to "hide" traffic.

**CWR - Congestion Window Reduced**, an acknowledgement of congestion notification \(ECE\).

**ECE - Explicit Congestion Notification**, notifies sender of network congestion, or that the remote side is ENC capable \(if sent along with SYN\).

**URG - Urgent field**, is valid in this transmission.

**ACK** - **Acknowledgement field**, is on almost all transmissions except for initial SYN.

**PSH** - Requests data be pushed to application.

**RST** - Resets the connection.

**SYN** - Requests a Seq No sync.

**FIN** - No more data to send.

## PSH vs URG

**PSH** - Force the receiver to push all data to the process immediately. Used for interactive things where keystrokes should be processed relatively quickly by Layer 7. Netcat does this to force writing to the terminal. Telnet is another example.

**URG** - Not well documented or implemented, but the urgent pointer indicates how much data is urgent at the beginning of the segment. Only the urgent data should be provided to the process in an out-of-band manner.

Neither has an API to actually set the value.

---

|[Next Topic](/06-osi-layer-4/syn-and-ack.md)|
|---|
