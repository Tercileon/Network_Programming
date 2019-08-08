<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" > Return to TOC </a>

# RST

Both RSTs and FINs \(eventually\) result in a teardown, but the previous state listing did not reference RST at all.

An RST can be thought of as aborting the connection \(i.e. ESTABLISHED directly to TIME-WAIT/CLOSED\).

For those with Linux experience, a good analogy is how 'kill -9' terminates a process regardless of what the process is currently doing.

In TCP, a RST usually takes the place of an ICMP Port Unreachable message for closed ports.

---

<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/06-osi-layer-4/traffic-control.md" > Continue to Next Topic </a>
