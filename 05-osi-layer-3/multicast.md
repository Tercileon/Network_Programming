|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## Multicast

## A global multicast address can be broken down as follows:

![](/assets/ipv6multicast.png)

[https://mrncciew.com/2013/04/05/ipv6-basics/](https://mrncciew.com/2013/04/05/ipv6-basics/)

[http://www.txv6tf.org/wp-content/uploads/2013/07/Martin-IPv6-Multicast-TM-v3.pdf](http://www.txv6tf.org/wp-content/uploads/2013/07/Martin-IPv6-Multicast-TM-v3.pdf)

| Address | Scope | Meaning |
| :--- | :--- | :--- |
| FF01::1 | Node-Local | All Nodes |
| FF01::2 | Node-Local | All Routers |
| FF02::1 | Link-Local | All Nodes |
| FF02::2 | Link-Local | All Routers |
| FF02::5 | Link-Local | OSPFv3 Routers |
| FF02::6 | Link-Local | OSPFv3 DR Routers |
| FF02::1:FFXX:XXXX | Link-Local | Solicited Node |

NOTE: This list is not exhaustive.

---

|[Next Topic](/05-osi-layer-3/anycast.md)|
|---|
