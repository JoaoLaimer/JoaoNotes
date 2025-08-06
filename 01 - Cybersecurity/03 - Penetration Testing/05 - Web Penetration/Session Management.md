## Session Management Life-cycle
#### Session Creation
The first step in the life cycle occurs only after the user provide their credentials. However, on many web applications, the session is already created when you visit the application. Once the session is created, you receive a session value that is then sent with each new request.

#### Session Tracking
Once you receive your session value, this is submitted with each new request. This allows the web application to track your actions even though the HTTP protocol is stateless in nature. With each request made, the web application can recover the session value from the request and perform a server-side lookup to understand who the session belongs to and what permissions they have. In the event that there are issues in the session tracking process, it may allow a threat actor to hijack a session or impersonate one.

#### Session Expiry
Because the HTTP protocol is stateless, it may happen that a user of the web application all of a sudden stops using it. For example, you might close the tab or your entire browser. Since the protocol is stateless, the web application has no method to know that this action has occurred. This is where session expiry comes into play. Your session value itself should have a lifetime attached to it. If the lifetime expires and you submit an old session value to the web application, it should be denied as the session should have been expired. Instead, you should be redirected to the login page to authenticate again and start the session management life-cycle all over again.

#### Session Termination
However, in some cases, the user might forcibly perform a logout action. In the event that this occurs, the web application should terminate the user's session. While this is similar to session expiry, it is unique in the sense that even if the session's lifetime is still valid, the session itself should be terminated. Issues in this termination process could allow a threat actor to gain persistent access to an account.


To understand the common vulnerabilities in session management, we first need to examine authentication and authorisation. While they sound the same and are often confused, each plays a critical and unique role in session management. To better explain the differences, review the IAAA model (Identification, [[Authentication]], [[Authorization]], [[Accounting]] )

## Cookie-Based Session Management
Once the web application wants to begin tracking, in a response, the Set-Cookie header value will be sent. Your browser will interpret this header to store a new cookie value. Let's take a look at such a Set-Cookie header:

`Set-Cookie: session=12345;`  

Your browser will create a cookie entry for a cookie named `session` with a value of `12345` which will be valid for the domain where the cookie was received from.
Other values can be added to this header, please refer [here](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Set-Cookie), but some of the noteworthy ones are:
- **Secure** - Indicates to the browser that the cookie may only be transmitted over verified HTTPS channels. If there are certificate errors or HTTP is used, the cookie value will not be transmitted.
- **HTTPOnly** - Indicates to the browser that the cookie value may not be read by client-side JavaScript.
- **Expire** - Indicates to the browser when a cookie value will no longer be valid and should be removed.
- **SameSite** - Indicates to the browser whether the cookie may be transmitted in cross-site requests to help protect against CSRF attacks.
A key thing to remember with cookie-based authentication is that the browser itself will decide when a certain cookie value will be sent with a request. After reviewing the domain and the attributes of the cookie, the browser makes this decision, and the cookie is attached automatically without any additional client-side JavaScript code.
## Token-Based Session Management
Instead of using the browser's automatic cookie management features, it relies on client-side code for the process. After authentication, the web application provides a token within the request body. Using client-side JavaScript code, this token is then stored in the browser's LocalStorage.
When a new request is made, JavaScript code must load the token from storage and attach it as a header. One of the most common types of tokens is JSON Web Tokens (JWT), which are passed through the `Authorization: Bearer` header.

### Benefits and Drawbacks

| **Cookie-Session Management**                                                                                                                         | **Token-Based Session Management**                                                                                                                                        |
| ----------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Cookie is automatically sent by the browser with each request                                                                                         | Token has to be submitted as a header with each request using client-side JavaScript                                                                                      |
| Cookie attributes can be used to enhance the browser's protection of the cookie                                                                       | Tokens do not have automatic security protections enforced and should, therefore, be safeguarded against disclosures                                                      |
| Cookies can be vulnerable to conventional client-side attacks such as CSRF, where the browser is tricked into making a request on behalf of the user. | As the token is not automatically added to any request and cannot be read from LocalStorage by other domains, conventional client-side attacks such as CSRF are blocked.  |
| As cookies are locked to a specific domain, it can be difficult to use them securely in decentralised web applications.                               | Tokens work well in decentralised web applications, as they are managed through JavaScript and can often contain all the information required to verify the token itself. |
## Securing Session Life-cycle
### Session Creation
Most vulnerable
- **Weak Session Values**: If the process of session creation is weak, an attacker can reverse engineer the session creation process and generate or guess session values.
- **Controllable Session Values**: If security measures are not enforced, such as verifying the token's signatures, a threat actor would be able to generate their own token.
- **Session Fixation**: If a session value is not adequately rotated once you authenticate,a suitably positioned threat actor could record it when you are still unauthenticated and wait for you to authenticate to gain access to your session. 
- **Insecure Session Transmission**: When the threat actor can control the URL where you will be redirected to post-authentication. This could allow the threat actor to hijack your session. This isn't just with custom implementation, Oracle's SSO solution had a [massive bug that allowed for this to happen](https://krbtgt.pw/oracle-oam-10g-session-hijacking/).
### Session Tracking
- **Authorization Bypass**: When there aren't sufficient checks being performed on whether a user is allowed to perform the action they requested. In essence, this fails to track the user's session and its associated rights correctly. It is also worth talking about the two types of authorisation bypasses:

	- Vertical bypass - You can perform an action that is reserved for a more privileged user
	- Horizontal bypass - You can perform an action you are allowed to perform, but on a dataset that you should not be allowed to perform the action on
 - **Insufficient Logging**
### Session Expiry
Session expiry only has a single vulnerability, which is when the expiry time for sessions are excessive.
### Session Termination
For session termination, the key issue is when sessions are not properly terminated server-side when the logout action is performed.