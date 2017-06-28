# HTTP Response
An HTTP response message is similar to a request message, it also consists of 3 parts:

- Status Line
- Header
- Message Body

### Section 1: HTTP Response: Status Line
- The status line is the first line of the response provided by the server
- It consists of 3 parts:
	- The **HTTP version**, in the same format as in the message request, e.g. HTTP/1.1
	- A response **status code**, providing the result of the request
	- An English **reasonn phrase**, describing the status code.
	- Example:
		- HTTP/1.1 200 OK
		- HTTP/2 404 Not Found

- **Status codes**, associated with the status line belonw to 1 of 5 categories:
	- 1XX (provisional response): a provisional response that requires the requestor to take additional action in order to continue.
	- 2XX (successful): the server successfully processed the request.
	- 3XX (redirected): further action is needed to fulfill the request.
	- 4XX (request error): there was likely an error in the quest which prevented the server from being able to process it.
	- 5XX (Server Error): The server had an internal error when trying to process the request.

### Section 2: HTTP Response Header
- The **header** allows the server to pass additional information about the response that cannot be placed in the status line.
- Header fields give information about the server and how to access the resource identified by the request URI. e.g.
	- Accept-Ranges:  Allow the server to indicate its acceptance of range requests for a resrouce.
	- Age : Estimate of the amount of time since the response was generated at the origin server.
	- Location: Redirects to a location other tahn the request URI for request completion or identification of a new resource.
	- Proxy-Authenticate: Allow the client to identify itself (or its user) to a proxy that requires authentication.

### Section 3: HTTP Response Message Body
- The **message body** in the response must also be preceded by a blank line.
- The reponse to a **HEAD request** does not include a message body. All other responses do include a message body, although it may by of 0 length.
- The requested resource, e.g, the actual HTML, is included in the mesage body of the response.