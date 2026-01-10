## Cross-Site Scripting (XSS)
Injects a malicious script into a trusted site to compromise the site's visitors.
1. Attacker identifies an input validation vulnerability within the website
2. Attacker crafts a URL to perform code injection against then trusted website
3. The trusted site returns a page containing the malicious code.
4. Malicious code runs in the client's browser with permission level as the trusted site.

- Defacing the trusted website
- Stealing the user's data
- Intercepting data or communications
- Installing malware on client's system
### Non-Persistent XSS
This type of attack only occurs when it's launched and happens once.
### Persistent XSS
Allows an attacker to insert code into the backend database used by the trusted website.
### Document Object Model (DOM) XSS
Exploits the client's web browser using client-side scripts to modify the content and layout of the web page.
## Session Management
Enables web application to uniquely identify a user across several different actions and requests.
### Non-Persistent
Known as a session cookie, which resides in memory and is used for a very shot period of time
## Persistent
Stored in the browser cache until either deleted by a user or expired.
## Session Hijacking
Type of spoofing attack where the attacker disconnects a host and then replaces it with his or her own machine by spoofing the original host IP.
## Session Prediction
Type of spoofing attack where the attacker attempts to predict the session token in order to hijack the session
Session tokens need to be generated using a non-predictable algorithm.
## Cross-Site Request Forgery (XSRF)
Malicious script is used to exploit a session started on another site within the same web browser.
- Use user-specific tokens in all form submission.
- Add randomness and prompt for additional infromation.
- Require users to enter their current password when changing their password.