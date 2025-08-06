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