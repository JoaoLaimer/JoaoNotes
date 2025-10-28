## HTTP/2
HTTP/2 use a completely binary protocol. This is a massive improvement over the older version since it allows any binary information to be sent in a way that is easier for machines to parse without making mistakes.
The HTTP/2 request has the following components:
- **Pseudo-headers:** HTTP/2 defines some headers that start with a colon `:`. Those headers are the minimum required for a valid HTTP/2 request. Some examples: `:method`, `:path`, `:scheme` and `:authority` pseudo-headers.
- **Headers:** After the pseudo-headers, we have regular headers like `user-agent` and `content-length`. Note that HTTP/2 uses lowercase for header names.
- **Request Body:** Like in HTTP/1.1, this contains any additional information sent with the request, like POST parameters, uploaded files and other data.

## HTTP/2 Desync
When a reverse proxy server content to the end user with HTTP/2 (frontend connection) but requests it from the backend servers by using HTTP/1.1 (backend connection), we talk about HTTP/2 downgrading. This type of implementation is still common nowadays, making it possible to reintroduce HTTP request smuggling in the context of HTTP/2, but only where downgrades to HTTP/1.1 occur.
Instead of dealing directly with HTTP/2, we send HTTP/2 requests in the frontend connection to influence the corresponding HTTP/1.1 request generated in the backend connection so that it causes an HTTP desync condition.

### H2.CL
The Content-Length header has no meaning for HTTP/2, since the length of the request body is specified unambiguously. But nothing stops us from adding a Content-Length header to an HTTP/2 request. If HTTP downgrades occur, the proxy will pass the added `content-length` header from HTTP/2 to the HTTP/1.1 connection, enabling a desync.

The proxy receives the HTTP/2 request on the frontend connection. When translating the request to HTTP/1.1, it simply passes the Content-Length header to the backend connection. When the backend web server reads the request, it acknowledges the injected Content-Length as valid. Since the injected Content-Length in our example is 0, the backend is tricked into believing this is a POST request without a body. Whatever comes after the headers (the original body of the HTTP/2 request) will be interpreted as the start of a new request. Since the word `HELLO` is not a complete HTTP/1.1 request, the backend server will wait until more data arrives to complete it.
The backend connection is now desynced. If another user sends a request, it will be concatenated to the `HELLO` value lingering in the backend connection.

### H2.TE
We can also add a "Transfer-Encoding: chunked" header to the frontend HTTP/2 request, and the proxy might also pass it to the backend HTTP/1.1 connection untouched. If the backend web server prioritises this header to determine the request body size, we can desync the backend connection once again.
The effect would be the same as with the H2.CL case. The first request is now a chunked request. The first chunk is of size 0, so the backend believes that's where it ends. The rest of the HTTP/2 request body will poison the backend connection, affecting the next upcoming request.

### CRLF injection
**CRLF** is the shorthand notation for a newline. **CR** stands for **Carriage Return**, equivalent to the character with ASCII code point `0xD`, also represented as the `\r` character. **LF** stands for **Line Feed**, the ASCII character with code point `0xA`, often represented as `\n`. CRLF is simply the sequence of both those characters `\r\n`, one after the other, and is used in HTTP/1.1 as a delimiter between headers, and also to separate the headers from the body (by using a double `\r\n`).

Since HTTP/2 packets can handle binary information, inserting any character in any request field is possible. This poses a problem when translating requests to HTTP/1.1, as some characters like `\r\n` represent delimiters between headers. If we can inject `\r\n` in an HTTP/2 header, it might get translated by the proxy into HTTP/1.1 directly, which will be interpreted as a header separator, thus allowing us to smuggle requests.

## Request Tunneling
In certain proxy implementations, each user will get its own backend connection to separate their request from others. Whenever this happens, an attacker won't be able to influence the requests of other users. At first sight, it would appear that we can't do much if confined to our own connection, but we can still smuggle requests through the frontend proxy and achieve some results.
#### Leaking Internal Headers
The simplest way to abuse request tunnelling is to get some information on how the backend requests look. In some scenarios, the frontend proxies may add headers to the requests before sending them to the backend. If we want to smuggle a specific request to the backend, we may need to add such headers for the request to go through.
To leak such headers, we can abuse any functionality in the backend application that reflects a parameter from the request into the response.

#### Bypassing Frontend Restriction
In some scenarios, you will find that the frontend proxy enforces restrictions on what resources can be accessed on the backend website. For example, imagine your website has an admin panel at `/admin`, but you don't want it accessible to everyone on the Internet. As a simple solution, you could enforce a restriction in the frontend proxy to disallow any attempt to access `/admin` without requiring any changes in the backend server itself.
A request tunnelling vulnerability would allow us to smuggle a request to the backend without the frontend proxy noticing, effectively bypassing frontend security controls.

#### Web Cache Poisoning
Even if we can't influence other users' connections directly, we may be able to use request tunnelling to poison server-side caching mechanisms, affecting users indirectly. This kind of attack has a high severity as it impacts all users visiting the website for as long as the cached content lasts. Given the right conditions, the poisoned cached content can have anything the attacker wants, including javascript payloads. This can be used to issue malicious redirects or even steal user sessions.
**Note:** Extreme care needs to be taken when testing web cache poisonings in real-world production systems, as they may affect the availability of the website if not conducted properly.

## h2c Smuggling
#### HTTP Version Negotiation
Web servers can offer the client many HTTP protocol versions in a single port. This is useful since you can't guarantee that users will have an HTTP/2-compliant browser. In this way, the server can offer the client both HTTP/1.1 and HTTP/2, and the client can select the version they want to use. This process is known as negotiation and is handled entirely by your browser.
The original HTTP/2 specification defined two ways to negotiate HTTP/2, depending on whether the communications were encrypted or not. The two methods used the following protocol identifiers:

- **h2:** Protocol used when running HTTP/2 over a TLS-encrypted channel. It relies on the Application Layer Protocol Negotiation (ALPN) mechanism of TLS to offer HTTP/2.
- **h2c:** HTTP/2 over cleartext channels. This would be used when encryption is not available. Since ALPN is a feature of TLS, you can't use it in cleartext channels. In this case, the client sends an initial HTTP/1.1 request with a couple of added headers to request an upgrade to HTTP/2. If the server acknowledges the additional headers, the connection is upgraded to HTTP/2.]
#### h2c Upgrades
When negotiating a cleartext HTTP/2 connection, the client will send a regular HTTP/1.1 request with the `Upgrade: h2c` header to let the server know it supports h2c. The request must also include an additional `HTTP2-Settings` header with some negotiation parameters that we won't discuss in detail. A compliant server will accept the upgrade with a `101 Switching Protocols` response. From that point, the connection switches to HTTP/2.
#### Tunneling Requests via h2c Smuggling
When an HTTP/1.1 connection upgrade is attempted via some reverse proxies, they will directly forward the upgrade headers to the backend server instead of handling it themselves. The backend server will perform the upgrade and manage communications in the new protocol afterwards. The proxy will tunnel any further communications between client and server but won't check their contents anymore, since it assumes the protocol changed to something other than HTTP. Since connections in HTTP/2 are persistent by default, we should be able to send other HTTP/2 requests, which will now go directly to the backend server through the HTTP/2 tunnel. This technique is known as **h2c smuggling**.