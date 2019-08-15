|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## SACK

RFCs 1017 and 2018 introduced/refined selective acknowledgements. It allows all segments received properly to be ACKed, resulting in only the missing/wrong data packet being re-sent.

To facilitate this, a SACK TCP Option header must be created and appended to the TCP header. Negotiation for the use of SACK is done at the beginning of the TCP connection.

It uses a "left edge" and "right edge" to pinpoint the missing data.

The ACKno will be the same as a non-SACK connection. The appended header will also include the SACK option for TCP indicating the other data it received. The sender may then re-transmit the missing data.

---

|[Next Topic](/06-osi-layer-4/tcp-handshake.md)|
|---|
