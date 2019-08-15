|[Table of Contents](/00-Table-of-Contents.md)|
|---|

---

## HTTP Responses

HTTP Responses conclude the transaction. Other transactions may be required to get other resources found on the page. Remember that \r\n separates the header from the actual data.

### Initial Response Line \(Status Line\)

The initial response line, called the status line, also has three parts separated by spaces: the HTTP version, a response status code that gives the result of the request, and an English reason phrase describing the status code. Typical status lines are:

> ```text
> HTTP/1.0 200 OK
> ```

or

> ```text
> HTTP/1.0 404 Not Found
> ```

Notes:

* The HTTP version is in the same format as in the request line, "**HTTP/x.x**".
* The status code is meant to be computer-readable; the reason phrase is meant to be human-readable, and may vary.

#### Example 1

`HTTP/1.1 200 OK`

`Date: Mon, 27Jul2009 12:28:53 GMT`

`Server: Apache/2.2.14 (Win32)`

`Last-Modified: Wed, 22 Jul 2009 19:15:56 GMT`

`Content-Length: 88`

`Content-Type: text/html`

`Connection: Closed`

#### Example 2

`HTTP/1.1 404 Not Found`

`Date: Sun, 18 Oct 2012 10:36:20 GMT`

`Server: Apache/2.2.14 (Win32)`

`Content-Length: 230`

`Connection: Closed`

`Content-Type: text/html; charset=iso-8859-1`

---

|[Next Topic](/07-osi-layer-7/http-status-codes.md)|
|---|
