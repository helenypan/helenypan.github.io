# HTTP Sessions and Cookies

### HTTP Sessions
- The HTTP cline(e.g. a browser) estabishes a TCP connection with a server (typically port 80), and initiates a request.
- The HTTP server, listening on the port, receives the request, processes it, and sends back a response. The response includes a **session ID**, and the server may store user information relates to this session.
- When the broswer makes another request, and includes the session ID, the server can reference previously stored information and respond accordingly.
- The **session ID** is typically a long randomly generated string sent back to the browser as a **cookie**.

### Cookies
- The **cookie** is stored in the browser, and sent back to the server with every request.
- Additional data, related to the session itself, can be stored in the cookie.
- If not managed properly, this information can lead to security vulnerabilities.

### Sessions and Cookies
- It's common in web applications to provide the session ID in the cookie, but to keep other information in a **session store** on the server side.
- A cookie can only store about 4Kb of data - sometimes this is not enough.
- Secret information should not be passed through cookies.
- The session store uses the session ID to keep track of data.
