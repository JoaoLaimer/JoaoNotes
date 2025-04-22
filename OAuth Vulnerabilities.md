## Identifying OAuth Usage in an Application
The first indication that an application uses OAuth is often found in the login process. Look for options allowing users to log in using external service providers like Google, Facebook, and GitHub. These options typically redirect users to the service provider's authorization page, which strongly signals that OAuth is in use.
## Detecting OAuth Implementation
When analyzing the network traffic during the login process, pay attention to HTTP redirects. OAuth implementations will generally redirect the browser to an authorization server's URL. This URL often contains specific query parameters, such as `response_type`, `client_id`, `redirect_uri`, `scope`, and `state`.
## Identifying the OAuth Framework

Once you have confirmed that OAuth is being used, the next step is to identify the specific framework or library the application employs. This can provide insights into potential vulnerabilities and the appropriate security assessments. Here are some strategies to identify the OAuth framework:

- **HTTP Headers and Responses**: Inspect HTTP headers and response bodies for unique identifiers or comments referencing specific OAuth libraries or frameworks.
- **Source Code Analysis**: If you can access the application's source code, search for specific keywords and import statements that can reveal the framework in use. For instance, libraries like `django-oauth-toolkit`, `oauthlib`, `spring-security-oauth`, or `passport` in `Node.js`, each have unique characteristics and naming conventions.
- **Authorization and Token Endpoints**: Analyze the endpoints used to obtain authorization codes and access tokens. Different OAuth implementations might have unique endpoint patterns or structures. For example, the `Django OAuth Toolkit` typically follows the pattern `/oauth/authorize/` and `/oauth/token/`, while other frameworks might use different paths.
- **Error Messages**: Custom error messages and debug output can inadvertently reveal the underlying technology stack. Detailed error messages might include references to specific OAuth libraries or frameworks.
## Stealing OAuth Token
### Role of Redirect_URI

The `redirect_uri` parameter is specified during the OAuth flow to direct where the authorization server should send the token after authorization. This URI must be pre-registered in the application settings to prevent open redirect vulnerabilities. During the OAuth process, the server checks that the provided `redirect_uri` matches one of the registered URIs.
#### Vulnerability
An insecure `redirect_uri` can lead to severe security issues. If attackers gain control over any domain or URI listed in the `redirect_uri`, they can manipulate the flow to intercept tokens.
If an attacker gains control over any redirect_uri registered, they can exploit the OAuth flow by setting the redirect_uri to the domain they control, the authorization server will send the token to this controlled domain.
The attacker can now capture this token and use it to access protected resources.
#### Preparing the Payload (Attacker Perspective)
The attacker can send a link with a malicious redirect and submits the request to a legitimate URL. The malicious redirect then intercepts the authorization code from the URL.
# CSRF in OAuth
The **state** parameter in the OAuth 2.0 framework protects against CSRF attacks, which occur when an attacker tricks a user into executing unwanted actions on a web application where they are currently authenticated. In the context of OAuth, CSRF attacks can lead to unauthorized access to sensitive resources by hijacking the OAuth flow.
#### Vulnerability of Weak or Missing State Parameter
For instance, consider an OAuth implementation where the state parameter is either **missing** or **predictable** (e.g., a static value like "state" or a simple sequential number). An attacker can initiate an OAuth flow and provide their malicious redirect URI. After the user authenticates and authorizes the application, the authorization server redirects the authorization code to the attacker's controlled URI, as specified by the weak or absent state parameter.