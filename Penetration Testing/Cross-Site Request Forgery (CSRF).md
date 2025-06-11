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