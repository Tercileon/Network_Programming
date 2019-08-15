|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## RST

Both RSTs and FINs \(eventually\) result in a teardown, but the previous state listing did not reference RST at all.

An RST can be thought of as aborting the connection \(i.e. ESTABLISHED directly to TIME-WAIT/CLOSED\).

For those with Linux experience, a good analogy is how 'kill -9' terminates a process regardless of what the process is currently doing.

In TCP, a RST usually takes the place of an ICMP Port Unreachable message for closed ports.

---

|[Next Topic](/06-osi-layer-4/traffic-control.md)|
|---|
