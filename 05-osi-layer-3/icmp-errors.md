<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" > Return to TOC </a>

# ICMP Errors

Below, I've captured some anecdotal reasons you will see some common ICMP errors. They are NOT absolutes, but just things to think about should you encounter them.

**Network unavailable typically means there is no route to the network.**

**Host unreachable is usually one of two reasons:**

* Layer 1 is broken, host physically offline.
* A security feature is preventing access to the host \(firewall, proxy, etc\).

**Port Unreachable is usually one of two reasons:**

* A security feature is preventing access to that port \(firewall, proxy, etc\).
* A service is likely not running on that port\*

**TTL Exceeded**

* Something is unusual about the route to the host that makes the path quite long.

**Reassembly Time Exceeded**

* I have never encountered this, however a severely degraded connection with multiple varying MTUs could theoretically cause this.

---

<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/05-osi-layer-3/icmp-header.md" > Continue to Next Topic </a>
