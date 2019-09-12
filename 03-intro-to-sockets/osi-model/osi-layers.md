|[Table of Contacts](/00-Table-of-Contents.md)|
|---|

---

## OSI Layers

![](/assets/84433547__Web.png)

## Layer 1 Physical -

Responsible for Media, Signal and Binary Transmission. Examples include hubs, repeaters, and Ethernet cables. Data is transmitted by an electric voltage, radio frequencies, infrared or light waves over fiber.

## **Layer 2 Data Link -** 

The Data Link layer checks for physical transmission errors, frame sychronization, and that data packets are encoded and decoded into bits. The Data Link layer also manages physical addressing schemes such as MAC addresses for Ethernet networks, because the Data Link layer is the single most complex layer in the OSI model, it is often divided into two parts, the "Media Access Control" sublayer and the "Logical Link Control" sublayer. The MAC sub layer controls how a computer on the network gains access to the network and permissions to transmit data. The LLC layer controls frame synchronization, flow control and error checking.

## Layer 3 Network -

Layer 3 provides switching and routing technologies, creating logical paths, known as virtual circuits, for transmitting data from node to node. Routing and forwarding are functions of this layer, as well as addressing, internetworking, error handling, congestion control and packet sequencing.

## Layer 4 Transport -

End-to-End Connections and Reliability. As the name implies, this layer moves data across network connections, usually using TCP. It also handles error recovery and re-transmissions.

## Layer 5 Session -

This layer establishes, manages and terminates connections between applications. The session layer sets up, coordinates, and terminates conversations, exchanges, and dialogues between the applications at each end. It deals with session and connection coordination.

## Layer 6 Presentation -

This layer is the simplest in function of any piece of the OSI model. At Layer 6, it handles syntax processing of message data such as format conversions and encryption / decryption needed to support the Application layer above it and Session layer below.

## Layer 7 Application -

This layer is the user interface responsible for displaying received information to the user. It supports application and end-user processes. The application layer is an abstraction layer that specifies the shared protocols and interface methods used by hosts in a communications network. Network process to application.

---

|[Next Topic](/03-intro-to-sockets/bsd-socket-api/README.md)|
|---|
