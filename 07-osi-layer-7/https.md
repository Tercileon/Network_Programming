|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## HTTPS

###  **HyperText Transfer Protocol Secure \(HTTPS\):**

An extension of the [Hypertext Transfer Protocol](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) \(HTTP\) for secure communication over a computer network, and is widely used on the Internet.

HTTPS pages typically use one of two secure protocols to encrypt communications - SSL \(Secure Sockets Layer\) or TLS \(Transport Layer Security\). Both the TLS and SSL protocols use what is known as an 'asymmetric' Public Key Infrastructure \(PKI\) system. An asymmetric system uses two 'keys' to encrypt communications, a 'public' key and a 'private' key. Anything encrypted with the public key can only be decrypted by the private key and vice-versa.

![](/assets/image-4.png)

When you request a HTTPS connection to a webpage, the website will initially send its SSL certificate to your browser. This certificate contains the public key needed to begin the secure session. Based on this initial exchange, your browser and the website then initiate the 'SSL handshake'. The SSL handshake involves the generation of shared secrets to establish a uniquely secure connection between yourself and the website.

When a trusted SSL Digital Certificate is used during a [HTTPS](https://www.instantssl.com/https-tutorials/what-is-https.html) connection, users will see a padlock icon in the browser address bar. When an Extended Validation Certificate is installed on a web site, the address bar will turn green.

### The major benefits of a HTTPS certificate are:

* Customer information, like credit card numbers, are encrypted and cannot be intercepted
* Visitors can verify you are a registered business and that you own the domain
* Customers are more likely to trust and complete purchases from sites that use HTTPS

---

|[Next Topic](/07-osi-layer-7/smtp.md)|
|---|
