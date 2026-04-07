CSRF is a type of security vulnerability where an attacker tricks a user's web browser into performing an unwanted action on a trusted site where the user is authenticated. This is achieved by exploiting the fact that the browser includes any relevant cookies (credentials) automatically, allowing the attacker to forge and submit unauthorised requests on behalf of the user (through the browser). The attacker's website may contain HTML forms or JavaScript code that is intended to send queries to the targeted web application.
## Cycle of CSRF

A CSRF attack has **three** essential phases:

- The attacker already knows the format of the web application's requests to carry out a particular task and sends a malicious link to the user.
- The victim's identity on the website is verified, typically by cookies transmitted automatically with each domain request and clicks on the link shared by the attacker. This interaction could be a click, mouse over, or any other action.
- Insufficient security measures prevent the web application from distinguishing between authentic user requests and those that have been falsified.

## Traditional CSRF

Conventional CSRF attacks frequently concentrate on state-changing actions carried out by submitting forms. The victim is tricked into submitting a form without realising the associated data like cookies, URL parameters, etc. The victim's web browser sends an HTTP request to a web application form where the victim has already been authenticated. These forms are made to transfer money, modify account information, or alter an email address.

## XMLHttpRequest CSRF
An asynchronous CSRF exploitation occurs when operations are initiated without a complete page request-response cycle. This is typical of contemporary online apps that leverage asynchronous server communication (via **XMLHttpRequest** or the **Fetch** API) and JavaScript to produce more dynamic user interfaces. These attacks use asynchronous calls instead of the more conventional form submissions. Still, they exploit the same trust relationship between the user and the online service.
The following is a simplified overview of the steps that an asynchronous CSRF attack could take: 

- The victim opens a session saved in their browser's cookies and logs into the `mailbox.thm`.      
- The attacker entices the victim to open a malicious webpage with a script that can send queries to the `mailbox.thm`.  
- To modify the user's email forwarding preferences, the malicious script on the attacker's page makes an AJAX call to `mailbox.thm/api/updateEmail` (using XMLHttpRequest or Fetch).
- The `mailbox.thm` session cookie is included with the AJAX request in the victim's browser.
- After receiving the AJAX request, mailbox.thm evaluates it and modifies the victim's settings if no CSRF defences exist.
## Basic CSRF - Hidden Link/Image Exploitation
A covert technique known as **hidden link/image exploitation** in CSRF involves an attacker inserting a 0x0 pixel image or a link into a webpage that is nearly undetectable to the user. Typically, the `src or href` element of the image is set to a destination URL intended to act on the user's behalf without the user's awareness.
This technique preys on authenticated sessions and utilises a social engineering approach when a user may inadvertently perform operations on a different website while still logged in.

## Double Submit Cookie Bypass
A CSRF token is a unique, unpredictable value associated with a user's session, ensuring each request comes from a legitimate source. One effective implementation is the **[Double Submit Cookies technique](https://cheatsheetseries.owasp.org/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.html#alternative-using-a-double-submit-cookie-pattern)**, where a cookie value corresponds to a value in a hidden form field. When the server receives a request, it checks that the cookie value matches the form field value, providing an additional layer of verification.

**Token Generation**: When a user logs in or initiates a session, the server generates a unique CSRF token.
**Form Submission**: Upon submitting the form, two versions of the CSRF token are sent to the server: one in the cookie and the other as part of the form data.
**Server Validation**: The server then checks if the CSRF token in the cookie matches the one sent in the form data. If they match, the request is considered legitimate and processed; if not, the request is rejected.

### Possible Vulnerable Scenarios
- **Session Cookie Hijacking (Man in the Middle Attack)**
- **Subverting the Same-Origin Policy (Attacker Controlled Subdomain)**: Browser vulnerabilities or deceiving the user into sending a request through an attacker-controlled subdomain with permission to set cookies for its parent domain could be used.
- **Exploiting XSS Vulnerabilities**: An attacker may be able to obtain the CSRF token from the cookie or the page itself if the web application is susceptible to Cross-Site Scripting (XSS).
- **Exploiting XSS Vulnerabilities**: An attacker may be able to obtain the CSRF token from the cookie or the page itself if the web application is susceptible to Cross-Site Scripting (XSS).
- **Subdomain Cookie Injection**: Injecting cookies into a user's browser from a related subdomain is another potentially sophisticated technique that might be used.

## SameSite Cookie Bypass
These cookies come with a special attribute designed to control when they are sent along with cross-site requests. Implementing the SameSite cookie property is a reliable safeguard against cross-origin data leaks, CSRF, and XSS attacks. Depending on the request's context, it tells the browser when to transmit the cookie. **Strict**, **Lax**, and **None** are the three potential values for the attribute.
- **Lax**: Lax SameSite cookies are like a friendly neighbour. They provide a moderate level of protection by allowing cookies to be sent in top-level navigations and safe HTTP methods like GET, HEAD, and OPTIONS. This means that cookies will not be sent with cross-origin POST requests, helping to mitigate certain types of CSRF attacks. However, cookies are still included in GET requests initiated by external websites, which may pose a security risk if sensitive information is stored in cookies.
- **Strict**: Strict SameSite cookies act as vigilant guards. They offer the highest level of protection by restricting cookies to be sent only in a first-party context. This means that cookies are only sent with requests originating from the same site that set the cookie, effectively preventing cross-site request forgery attacks. By enforcing strict isolation between different origins, strict SameSite cookies significantly enhance the security of web applications, especially in scenarios where sensitive user data is involved.
- **None**: None SameSite cookies behave like carefree globetrotters. They are sent with both first-party and cross-site requests, making them convenient for scenarios where cookies need to be accessible across different origins. However, to prevent potential security risks associated with cross-site requests, None SameSite cookies require the **Secure** attribute if the request is made over HTTPS. This ensures that cookies are only transmitted over secure connections, reducing the likelihood of interception or tampering by malicious actors during transit.

## XMLHttpRequest Exploitation

In the context of an AJAX request, CSRF is like someone making your web browser unknowingly send a request to a website where you're logged in. It's as if someone tricked your browser into doing something on a trusted site without your awareness, potentially causing unintended actions or changes in your account. CSRF attacks can still succeed even when AJAX requests are subject to the [Same-Origin Policy (SOP)](https://en.wikipedia.org/wiki/Same-origin_policy), which typically forbids cross-origin requests.

## Same Origin Policy (SOP) and Cross-Origin Resource Sharing (CORS) Bypass

[CORS and SOP](https://tryhackme.com/r/room/corsandsop) bypass to launch CSRF is like an attacker using a trick to make your web browser send requests to a different website than the one you're on. Under an appropriate CORS policy, certain requests could only be submitted by recognised origins. However, misconfigurations in CORS policies can allow attackers to circumvent these limitations if they rely on origins that the attacker can control or if credentials are included in cross-origin requests.


## Hunting for CSRF
First look for state-changing actions like, password changes, sending emails, deleting emails, etc.
Look for lack of CSRF Protections, no CSRF Tokens or state tokens.
Confirm the vulnerability, craft an HTML page, and make sure to save with the .html extension. 
```html
<html>
	<form method="POST" action="https://email.example.com/password-change" id="csrf-form">
		<input type="text" name="new_password" value="abc123">
		<input type="submit" value="Submit">
	</form>
	<script>document.getElementById("csrf-form").submit();</script>
</html>
```
Open the HTML page in the browser that is signed into your target site. Check if your password on the target has been changed to abc123. 

### Bypassing CSRF Protecitons
#### Exploit Clickjacking
If the endpoint uses CSRF tokens but the page itself is vulnerable to click-jacking, you can exploit the clickjacking to achieve the same results as a CSRF. 
#### Change the Request Method 
#### Bypass CSRF Tokens Stored on the Server
Check if site is validating the tokens. First try deleting it. Second try a blank CSRF parameter.
#### Bypass Double-Submit Tokens 
Sometimes the server only checks if they are equal.
#### Bypass CSRF Referrer Header Check
Host a site with the victim site as a subdomain:
```
Referer: example.com.attacker.com
```
Or as a pathname:
```
Referer: attacker.com/example.com
```
