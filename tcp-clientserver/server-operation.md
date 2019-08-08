# Client/Server Operation

Server creates a socket, binds it to some well-known port number, and starts listening. 

Client creates a socket and tries to connect it to the server \(through the above port\). 

Server-client exchange some data. 

Close the connection \(of course the server continues to listen for more clients\)

