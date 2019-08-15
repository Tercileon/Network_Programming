|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## Lab 5-1

### HTTP Client and Server in C

Some of the standardized RFCs are:

HTTP/1.1 →Initially it is [RFC 2616](http://www.rfc-editor.org/info/rfc2616) but later replaced by [RFC 7230](http://www.rfc-editor.org/info/rfc7230), [RFC 7231](http://www.rfc-editor.org/info/rfc7231), [RFC 7232](http://www.rfc-editor.org/info/rfc7232), [RFC 7233](http://www.rfc-editor.org/info/rfc7233), [RFC 7234](http://www.rfc-editor.org/info/rfc7234), [RFC 7235](http://www.rfc-editor.org/info/rfc7235). So, we need to read from RFC 7230 to RFC 7235 to implement basic workings of HTTP.

HTTP/2 → [RFC 7540](http://www.rfc-editor.org/info/rfc7540) and [RFC 7541](http://www.rfc-editor.org/info/rfc7541)

#### HTTP Server:

1. Create
2. Define
3. Bind
4. Listen
5. Accept
6. Send/Receive
7. Close

A socket, `server_fd`, is created with the _socket_ system call:

```text
int server_fd = socket(domain, type, protocol);
```

Domain - Address Family: AF\_INET\(IPv4\) \|  AF\_INET6 \(IPv6\)

Type: SOCK\_STREAM \(TCP\)  \|  SOCK\_DGRAM \(UDP\)  \|  SOCK\_RAW \(RAW\)

Protocol - Only used for specific Address Families that support multiple protocols.

**Create:**

```text
#include <sys/socket.h>
...
...
if ((server_fd = socket(AF_INET, SOCK_STREAM, 0)) < 0) 
{
    perror(“cannot create socket”); 
    return 0; 
}
```

**Define and Bind:**

```text
struct sockaddr_in address;
const int PORT = 8080; 

memset((char *)&address, 0, sizeof(address)); 
address.sin_family = AF_INET; 
address.sin_addr.s_addr = htonl(INADDR_ANY); //0.0.0.0
address.sin_port = htons(PORT); 

if (bind(server_fd,(struct sockaddr *)&address,sizeof(address)) < 0) 
{ 
    perror(“bind failed”); 
    return 0; 
}
```

**Listen:**

```text
int listen(int socket, int backlog);
```

**Accept:**

```text
                1                                  2                              3     
int accept(int socket, struct sockaddr *restrict address, socklen_t *restrict address_len);
```

1. Socket created for accepting connection in the _listen_ function.
2. The address structure that gets filed in with the client's IP.
3. Length of the Address Structure.

```text
if (listen(server_fd, 3) < 0) //error handling
{ 
    perror(“In listen”); 
    exit(EXIT_FAILURE); 
}
```

```text
if ((new_socket = accept(server_fd, (struct sockaddr *)&address, (socklen_t*)&addrlen))<0)
{
    perror("In accept");            //error handling
    exit(EXIT_FAILURE);        
}
```

![](/assets/image-3.png)

![](/assets/image-5.png)

If we want to send `Hello from server`, first we need to construct the **Header**. Then insert a **blank line**, then we can send our message/data.

The headers shown above are just an example. In fact there are many Headers present in HTTP. You can take a look at the HTTP RFCs → [RFC 7230](http://www.rfc-editor.org/info/rfc7230), [RFC 7231](http://www.rfc-editor.org/info/rfc7231), [RFC 7232](http://www.rfc-editor.org/info/rfc7232), [RFC 7233](http://www.rfc-editor.org/info/rfc7233), [RFC 7234](http://www.rfc-editor.org/info/rfc7234), [RFC 7235](http://www.rfc-editor.org/info/rfc7235).

Now, we will construct a minimal HTTP Header to make our server work.

```text
char *hello = "HTTP/1.1 200 OK\nContent-Type: text/plain\nContent-Length: 12\n\nHello world!";
```

These 3 Headers are the minimum required.

1. `HTTP/1.1 200 OK` → This mentions what version of HTTP we are using, Status code and Status message.
2. `Content-Type: text/plain` → This says that I’m \(server\) sending a plain text. There are many `Content-Type`s. For example, for images we use [this](https://msdn.microsoft.com/en-us/library/ms527550%28v=exchg.10%29.aspx).
3. `Content-Length: 12` → It mentions how many bytes the server is sending to the client. The web-browser only reads how much we mention here.

The next part is the `Body`where we send our data.

First we need to calculate how many bytes we are sending in Body. Then we mention that in `Content-Length`. Also, we set the `Content-Type` appropriately according to the data we are sending.

#### [Content-Types:](https://msdn.microsoft.com/en-us/library/ms526508%28v=exchg.10%29.aspx)

The two composite top-level media types are:

*  Multipart
*  Message

The five discrete top-level media types are:

*  Text                                   
*  Image
*  Audio
*  Video
*  Application

#### Send/Receive:

Communication is the easy part. The same _`read`_ and _`write`_ system calls that work on files also work on sockets.

```text
char buffer[30000] = {0};
valread = read( new_socket , buffer, 30000);
printf("%s\n",buffer );
write(new_socket , hello , strlen(hello));
printf("------------------Hello message sent-------------------");
close(new_socket);
```

#### Close:

```text
close(new_socket);
```

#### HTTP Server:

1. Create
2. Define
3. Bind
4. Listen
5. Accept
6. Send/Receive
7. Close

```text
#include <stdio.h>
#include <sys/socket.h>
#include <unistd.h>
#include <stdlib.h>
#include <netinet/in.h>
#include <string.h>

#define PORT 8080
int main(int argc, char const *argv[])
{
    int server_fd, new_socket; long valread;
    struct sockaddr_in address;
    int addrlen = sizeof(address);
    
    char *hello = "HTTP/1.1 200 OK\nContent-Type: text/plain\nContent-Length: 12\n\nHello world!";
    
    // Create Socket
    if ((server_fd = socket(AF_INET, SOCK_STREAM, 0)) == 0)
    {
        perror("In socket");
        exit(EXIT_FAILURE);
    }
    
    // Define
    address.sin_family = AF_INET;
    address.sin_addr.s_addr = INADDR_ANY;
    address.sin_port = htons( PORT );
    
    memset(address.sin_zero, '\0', sizeof address.sin_zero);
    
    // Bind
    if (bind(server_fd, (struct sockaddr *)&address, sizeof(address))<0)
    {
        perror("In bind");
        exit(EXIT_FAILURE);
    }
    // Listen
    if (listen(server_fd, 10) < 0)
    {
        perror("In listen");
        exit(EXIT_FAILURE);
    }
    while(1)
    {
        printf("\n+++++++ Waiting for new connection ++++++++\n\n");
        // Accept
        if ((new_socket = accept(server_fd, (struct sockaddr *)&address, (socklen_t*)&addrlen))<0)
        {
            perror("In accept");
            exit(EXIT_FAILURE);
        }
        // Send and Receive
        char buffer[30000] = {0};
        valread = read( new_socket , buffer, 30000);
        printf("%s\n",buffer );
        write(new_socket , hello , strlen(hello));
        printf("------------------Hello message sent-------------------");
        // Close
        close(new_socket);
    }
    return 0;
}
```

#### HTTP Client:

```text
#include <stdio.h>
#include <sys/socket.h>
#include <stdlib.h>
#include <unistd.h>
#include <netinet/in.h>
#include <string.h>
#include <arpa/inet.h>

#define PORT 8080

int main(int argc, char const *argv[])
{
    int sock = 0; long valread;
    struct sockaddr_in serv_addr;
    char *hello = "Hello from client";
    char buffer[1024] = {0};
    if ((sock = socket(AF_INET, SOCK_STREAM, 0)) < 0)
    {
        printf("\n Socket creation error \n");
        return -1;
    }
    
    memset(&serv_addr, '0', sizeof(serv_addr));
    
    serv_addr.sin_family = AF_INET;
    serv_addr.sin_port = htons(PORT);
    
    // Convert IPv4 and IPv6 addresses from text to binary form
    if(inet_pton(AF_INET, "127.0.0.1", &serv_addr.sin_addr)<=0)
    {
        printf("\nInvalid address/ Address not supported \n");
        return -1;
    }
    
    if (connect(sock, (struct sockaddr *)&serv_addr, sizeof(serv_addr)) < 0)
    {
        printf("\nConnection Failed \n");
        return -1;
    }
    send(sock , hello , strlen(hello) , 0 );
    printf("Hello message sent\n");
    valread = read( sock , buffer, 1024);
    printf("%s\n",buffer );
    return 0;
}
```

---

|[Next Topic](/07-osi-layer-7/layer-7-labs.md)|
|---|
