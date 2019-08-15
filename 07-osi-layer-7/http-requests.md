|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

### **HTTP Requests**

* The only MANDATORY parts of an HTTP Request are the METHOD, the URL, HTTP version, and the host \(and any data you need to send if POSTING\).
* We will only discuss the methods GET and POST because they are almost exclusively what you will encounter, however others do exist.

## Initial Request Line

The initial line is different for the request than for the response. A request line has three parts, separated by spaces: a method name, the local path of the requested resource, and the version of HTTP being used. A typical request line is:

> ```text
> GET /path/to/file/index.html HTTP/1.0
> ```

Notes:

* **GET** is the most common HTTP method; it says "give me this resource". \(Method names are always uppercase.\)
* The path is the part of the URL after the host name, also called the request URI \(a URI is like a URL, but more general\).
* The HTTP version always takes the form "**HTTP/x.x**", uppercase.

#### Example 1

`GET /hello.htm HTTP/1.1`

`User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT)`

`Host: www.example.com`

`Accept-Language:en-us`

`Accept-Encoding:gzip, deflate`

`Connection: Keep-Alive`

#### Example 2

`POST /cgi-bin/process.cgi HTTP/1.1`

`User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT)`

`Host: www.tutorialspoint.com`

`Content-Type: application/x-www-form-urlencoded`

`Content-Length: length`

`Accept-Language:en-us`

`Accept-Encoding:gzip, deflate`

`Connection: Keep-Alive`

**HTTP Methods \(Verbs\):**

GET is the default method used by the HTTP.

[There are 9 HTTP methods.](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods)

Some of them are:

1. GET — Fetch a URL
2. HEAD — Fetch information about a URL
3. PUT — Store to a URL
4. POST — Send form data to a URL and get a response back
5. DELETE — Delete a URL GET and POST \(forms\) are commonly used

REST APIs use GET, PUT, POST, and DELETE.

#### Safe methods

Some of the methods \(for example, HEAD, GET, OPTIONS and TRACE\) are, by convention, defined as safe, which means they are intended only for information retrieval and should not change the state of the server.

### POST

```text
POST /index.html HTTP/1.1
```

When a web browser sends a POST request from a web form element, the default Internet media type is "application/x-www-form-urlencoded". This is a format for encoding key-value pairs with possibly duplicate keys. Each key-value pair is separated by an '&' character, and each key is separated from its value by an '=' character. Keys and values are both escaped by replacing spaces with the '+' character and then using URL encoding on all other non-alphanumeric characters.

For example, the key-value pairs

```text
Name: Gareth Wylie
Age: 24
Formula: a + b == 13%!
```

are encoded as

```text
Name=Gareth+Wylie&Age=24&Formula=a+%2B+b+%3D%3D+13%25%21
```

Starting with HTML 4.0, forms can also submit data in [multipart/form-data](https://en.wikipedia.org/wiki/Multipart/form-data) as defined in [RFC 2388](https://tools.ietf.org/html/rfc2388) 

#### Examples:

A simple form using the default `application/x-www-form-urlencoded` content type:

```text
POST / HTTP/1.1
Host: foo.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 13

say=Hi&to=Mom
```

A form using the `multipart/form-data` content type:

```text
POST /test.html HTTP/1.1 
Host: example.org 
Content-Type: multipart/form-data;boundary="boundary" 

--boundary 
Content-Disposition: form-data; name="field1" 

value1 
--boundary 
Content-Disposition: form-data; name="field2"; filename="example.txt" 

value2
```

---

|[Next Topic](/07-osi-layer-7/http-responses.md)|
|---|
