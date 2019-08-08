<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" rel="Return to TOC"> Return to TOC </a>

# Networks and Ports

## Networks and Ports

![](../.gitbook/assets/1.PNG)

### Two Main Issues

* Addressing - Specifying a remote computer and service 
* Data transport - Moving bits back and forth

![](../.gitbook/assets/2.PNG)

#### Each endpoint of a network connection is always represented by a host \(URL/Domain/IP\) and port.

#### Ports are how processes get access to the network.

#### In Python you write it out as a tuple \(host, port\)

* **\("www.python.org", 80\)**
* **\("205.172.13.4", 443\)**

#### In all of the network programs you’ll write, you use this convention to specify a network address.

## **Common Ports** 

![](../.gitbook/assets/ports.PNG)

### Port numbers &lt; 1024 are considered "privileged" ports

* **Processes must have root/admin privileges to bind to these ports**
* **They are typically reserved for servers. IANA maintains the list of well known ports**
* **\(see references:** [**http://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml**](http://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)**\)**

### Ports &gt;= 1024 can be used by anyone

### If you do not bind to a port as a TCP client/UDP sender, you will get a random high number port automatically assigned to your process. This is called an “ephemeral port”.

---
<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/02-intro-to-networking/numbering-systems.md" > Continue to Next Topic </a>
