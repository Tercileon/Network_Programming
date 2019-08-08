<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/00-Table-of-Contents.md" rel="Return to TOC"> Return to TOC </a>

# Client/Server Model

## Client/Server Model

* Servers wait for incoming connections and provide a service \(e.g., web, mail, etc.\) 
* Clients make connections to servers
* Each endpoint is a running program

  ![](../../.gitbook/assets/client_server.PNG)

## Request/Response Cycle

**Most network programs use a request/ response model based on messages** 

* Client sends a request message \(e.g., HTTP\)

### _GET /index.html HTTP/1.0_ 

* Server sends back a response message

### _HTTP/1.0 200 OK_ 

### _Content-type: text/html_ 

### _Content-length: 48823 &lt;HTML&gt;_

### _..._ 

* The exact format depends on the application
* Close the connection \(of course the server continues to listen for more clients\)

---
<a href="https://github.com/CyberTrainingUSAF/08-Network-Programming/blob/master/03-intro-to-sockets/bsd-socket-api/major-system-calls.md" > Continue to Next Topic </a>
