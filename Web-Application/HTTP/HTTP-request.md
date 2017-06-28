# HTTP Request

### Section 1: HTTP Client Side: Request Line
- The request line identifies the resource, and the desired action ("request", "verb" or "method") that should be applied to it.
- The resource is typically identified by a Universal Resource Identifier (URI). 
	- Note: a Uniform Resource Locator(URL) is a specific type of URI.
- There are 9 request types that can be specified:
	1. **HEAD** : the response the resource would supply to a GET request, but without the response body.
	2. **GET**: return a representation of the resource.
	3. **POST**: submit data(e.g. from a HTML form) to the resource, where the data is supplied in the body of the request, and the result may be the creation of a new resource, or the update of an existing one.
	4. **PUT**: submit a representation of the resource to the server.
	5. **DELETE**: delete the resource.
	6. **TRACE**: echoes back the received requested.
	7. **OPTIONS**: returns the HTTP methods that the server supports for the specified resource.
	8. **CONNECT**: converts the request connection to a transparent TCP/IP tunnel(usually to facilitate SSL through HTTPS).
	9. **PATCH**: apply partial modifications to a resource.
- **Safe Methods**
	- HEAD, GET, OPTIONS and TRACE are referred to as safe methods.
	- safe methods should not produce side effects on the server.
	- Note: if a GET method is implemented in a safe way, a browser can make arbitrary GET requests withougt modifying the state of a web application. i.e. these requests can be cached.
- **Not Safe Methods**
	- POST, PUT and DELETE methods may cause side effects on the server, they are not considered safe.
	- Furthermore, the PUT and DELETE methods should be **idempotent** - multiple identical requests should have the same effect as a single request. So if you put a resource multiple times, it should continue to override it. If you delete a resource multiple times, it should be deleted the first time.

### Section 2: HTTP Client Side: Headers
- the HTTP message header is the primary part of an HTTP request
- Header fields syntax: field_name: field_value, e.g.
	- Accept: text/pain
	- Accept-Language: en-US
- An HTTP message header must be separated from the message body by a blank line.

### Section 3: HTTP Client Side: Message Body
- The message body in an HTTP request is optional
- It typically includes user-entered data or files taht are being uploaded.
- If an HTTP request includes a body, there are usually header fields that describe the body, e.g.
	- Content-Type: text/html
	- Content-Length: 3495