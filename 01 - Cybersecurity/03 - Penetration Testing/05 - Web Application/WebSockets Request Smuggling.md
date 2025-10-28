## What is a WebSocket?

When using HTTP, the client must make a request before the server can send any information. This complicates the implementation of some application features that require bidirectional communications. For example, suppose you are implementing a web application that needs to send real-time notifications to the user. Since the server can't push information to the user at will, the client would need to constantly poll the server for notifications, requiring lots of wasted requests.

The WebSocket protocol allows the creation of two-way communication channels between a browser and a server by establishing a long-lasting connection that can be used for full-duplex communications.
## Upgrading HTTP connections to Websockets
The WebSocket protocol was designed to be fully compatible with HTTP. Establishing a WebSocket connection follows a process similar to that of h2c. The client sends an initial HTTP request with an `Upgrade: websocket` header and other additional headers. If the server supports WebSockets, it responds with a `101 Switching Protocols` response and upgrades the connection accordingly. From that point onwards, the connection uses the WebSocket protocol instead of HTTP.
If we now add a proxy in the middle, something interesting happens: Instead of fronting the connections themselves, most proxies won't handle the upgrade but will instead relay them to the backend server. Once the connection is upgraded, the proxy will establish a tunnel between the client and server, so any further WebSocket traffic is forwarded without interruptions.

### Smuggling HTTP request through broken WebSocket Tunnels
To smuggle requests through a vulnerable proxy, we can create a malformed request such that the proxy thinks a WebSocket upgrade is performed, but the backend server doesn't really upgrade the connection. This will force the proxy into establishing a tunnel between client and server that will go unchecked since it assumes it is now a WebSocket connection, but the backend will still expect HTTP traffic.
One way to force this is to send an upgrade request with an invalid `Sec-Websocket-Version` header. This header is used to specify the version of the WebSocket protocol to use and will normally take the value of `13` in most current WebSocket implementations. If the server supports the requested version, it should issue a `101 Switching Protocols` response and upgrade the connection.

But we aren't interested in upgrading the connection. If we send an unsupported value for the `Sec-Websocket-Version` header, the server will send a `426 Upgrade Required` response to indicate the upgrade was unsuccessful.

Some proxies may assume that the upgrade is always completed, regardless of the server response. This can be abused to smuggle HTTP requests once again by performing the following steps:

1. The client sends a WebSocket upgrade request with an **invalid** version number.
2. The proxy forwards the request to the backend server.
3. The backend server responds with `426 Upgrade Required`. The connection doesn't upgrade, so the backend remains using HTTP instead of switching to a WebSocket connection.
4. The proxy doesn't check the server response and assumes the upgrade was successful. Any further communications will be tunnelled since the proxy believes they are part of an upgraded WebSocket connection.
### Bypassing Proxy Restrictions
```shell
GET /socket HTTP/1.1
Host: MACHINE_IP:8001
Sec-WebSocket-Version: 777
Upgrade: WebSocket
Connection: Upgrade
Sec-WebSocket-Key: nf6dB8Pb/BLinZ7UexUXHg==

GET /flag HTTP/1.1
Host: MACHINE_IP:8001
```

## Defeating Secure Proxies
#### Tricking the Proxy
While we won't be able to do this for all applications, if our target app has some vulnerability that allows us to proxy requests back to a server we control as attackers, we might be able to inject the `101 Switching Protocols` response to an arbitrary request. In these special cases, we should be able to smuggle requests through a fake WebSocket connection again.
#### Leveraging SSRF
```python
import sys
from http.server import HTTPServer, BaseHTTPRequestHandler

if len(sys.argv)-1 != 1:
    print("""
Usage: {} 
    """.format(sys.argv[0]))
    sys.exit()

class Redirect(BaseHTTPRequestHandler):
   def do_GET(self):
       self.protocol_version = "HTTP/1.1"
       self.send_response(101)
       self.end_headers()

HTTPServer(("", int(sys.argv[1])), Redirect).serve_forever()
```
