<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" > Return to TOC </a>

# SYN and ACK

Sequence numbers indicate the most recent piece of data sent.

Acknowledgement numbers indicate the next byte expected.

**During the initial handshake:**

* Host A randomly generates a sequence number.
* Host B will acknowledge A's seq number, and generate a randomseqno of it's own.
* Host A will acknowledge B's seq number and the connection is established.

**With NO DATA transmitted \(e.g. keep alive packet, or a one-sided series of transactions\):**

* A sender that is simply ACKing and not sending data of it's own, will re-use the same Sequence Number.
* Sequence Numbers may be re-acked until other side actually sends some data.

**During normal data transmission:**

* Sequence numbers mark the beginning of most recent data sent. It starts at the random number chosen during the handshake and is cumulative.
* Acknowledgement numbers =seqnumber + datarecv'd since last ACK + 1.

**Errors will result in the Acknowledgement number being set to the last successfully received CONTIGUOUS block of data + 1.**

* A sends 10 data, with as eq of 1, but B only receives 1-7, the Ack number will be 8.
* A sends 10 data, with as eq of 1, but B only receives 1 and 4-10, the Ack number will be 2.

---

<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/06-osi-layer-4/sack.md" > Continue to Next Topic </a>
