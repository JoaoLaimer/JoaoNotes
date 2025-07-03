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
5. **Access-Control-Allow-Credentials**: This header instructs the browser whether to expose the response 