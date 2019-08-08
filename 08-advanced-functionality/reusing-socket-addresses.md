<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" > Return to TOC </a>

# Reusing Socket Addresses

![](../.gitbook/assets/sockopt.PNG)

There might be situations when you force the program to terminate and you want to restart it immediately after that. As a result of the ﬁrst program execution, the socket might be in a TIME WAIT state. It cannot be immediately reused and an error will be raised.

This is the mechanism that should ensure that two different TCP sessions are not mixed up in the case that there are delayed packets belonging to the ﬁrst TCP session. Usually, this protection mechanism is not necessary because severe packet delays are not very likely in common networks. If you want to avoid seeing the 'address in use' error you can do it by setting the reuse address socket optionor simply change the port number:

## `s.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)`

**Reference:** [https://docs.python.org/2/library/socket.html](https://docs.python.org/2/library/socket.html)

---

<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/08-advanced-functionality/setsockopt-getsockopt.md" > Continue to Next Topic </a>
