# HTTP Overview

### HTTP Protocol

- Used to deliver resources in distributed hypermedia information systems.
- In order to build an debug web applications, it is vital to have a good understanding of how HTTP works.

### HTTP Resources
- Hypertext: Text, marked up using Hyper Text Markup Language (HTML), possibly styled with CSS, and containing references (i.e., hyperlinks) to other resources. 
- Hypermedia: The logical extension of hypertext to graphics, audio and video.
- Hyperlinks: Define a structure over the World Wide Web.
- Scripts: Code that can be executed on the client side (e.g. JavScript)

### HTTP Background
- HTTP/0.9: with HTTP/0.9, a client could only issue GET requests, asking a server for a resource.
	- e.g. GET /welcome.html, will cause the server to return the contents of the requested file (the response was required to be HMTL).
- HTTP/1.0 protocol, introduced in 1996, extended HTTP/0.9 to include request headers along with additional request methods.
- HTTP/1.1, included a number of improvements, most of them were aimed at making the web application more responsive.
	- Faster response, by allowing multiple transactions to take place over a single persistent connection.
	- Faster response and bandwidth savings, by adding cache support.
	- Faster reponse for dynamically-generated content, by supporting chunked encoding, which allows a response to be sent before its total length is known.
	- Efficient use of IP addresses, multiple domains can be served from a single IP address.
	- Support for proxies. 
	- Support for content negotiations.

- HTTP/2, was published in 2015, mainly aimed at performance improvements.
	- Data compression of HTTP headers.
	- Server push technologies.
	- Pipelining of requests.
	- Multiplexing multiple requests over a single TCP connection.
