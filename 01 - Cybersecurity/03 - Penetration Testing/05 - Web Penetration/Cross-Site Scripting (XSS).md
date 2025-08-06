## Types of XSS

- **Reflected XSS**: This attack relies on the user-controlled input reflected to the user. For instance, if you search for a particular term and the resulting page displays the term you searched for (**_reflected_**), the attacker would try to embed a malicious script within the search term.
- **Stored XSS**: This attack relies on the user input stored in the website’s database. For example, if users can write product reviews that are saved in a database (**_stored_**) and being displayed to other users, the attacker would try to insert a malicious script in their review so that it gets executed in the browsers of other users.
- **DOM-based XSS**: This attack exploits vulnerabilities within the Document Object Model (**DOM**) to manipulate existing page elements without needing to be reflected or stored on the server. This vulnerability is the least common among the three.
## Implications of XSS
There are many implications of XSS. Below, we list a few of them.

**Session hijacking**
As XSS can be used to steal session cookies, attackers can take over the session and impersonate the victim if successful.

**Phishing and credential theft**
Leveraging XSS, attackers can present a fake login prompt to the user. In one recent case, the browser’s page was partially hidden by a dialogue box requesting users to connect to their cryptocurrency wallet.

**Social engineering**
Using XSS, an attacker can create a legitimate-looking pop-up or alert within a trusted website. This can trick users into clicking malicious links or visiting malicious websites.

**Content manipulation and defacement**
In addition to phishing and social engineering, an attacker might use XSS to change the website for other purposes, such as inflicting damage on the company’s reputation.

**Data exfiltration**
XSS can access and exfiltrate any information displayed on the user’s browser. This includes sensitive information such as personal data and financial information.

**Malware installation**
A sophisticated attacker can use XSS to spread malware. In particular, it can deliver drive-by download attacks on the vulnerable website.

## Reflected XSS
**Reflected XSS** is a type of XSS vulnerability where a malicious script is reflected to the user’s browser, often via a **crafted URL** or **form submission**. Consider a search query containing `<script>alert(document.cookie)</script>`; many users wouldn’t be suspicious about such a URL, even if they look at it up close. If processed by a vulnerable web application, it will be executed within the context of the user’s browser.

## Stored XSS
Stored XSS, or Persistent XSS, is a web application security vulnerability that occurs when the application stores user-supplied input and later embeds it in web pages served to other users without proper sanitization or escaping. Examples include web forum posts, product reviews, user comments, and other data stores. In other words, stored XSS takes place when user input is saved in a data store and later included in the web pages served to other users without adequate escaping.

## Context

The injected payload will most likely find its way within one of the following:

- Between HTML tags
- Within HTML tags
- Inside JavaScript

When XSS happens between HTML tags, the attacker can run `<script>alert(document.cookie)</script>`.

However, when the injection is within an HTML tag, we need to end the HTML tag to give the script a turn to load. Consequently, we might adapt our payload to `><script>alert(document.cookie)</script>` or `"><script>alert(document.cookie)</script>` or something similar that would fit in the context.

If your code is within a JavaScript string, you can close the string with `'`, complete the command with a semicolon, execute your command, and comment out the rest of the line with `//`. You can try something like this `';alert(document.cookie)//`

## Evasion
Various repositories can be consulted to build your custom XSS payload. This gives you plenty of room for experimentation. One such list is the [XSS Payload List](https://github.com/payloadbox/xss-payload-list).
However, sometimes, there are filters blocking XSS payloads. If there is a limitation based on the payload length, then [Tiny XSS Payloads](https://github.com/terjanq/Tiny-XSS-Payloads) can be a great starting point to bypass length restrictions.

If XSS payloads are blocked based on specific blocklists, there are various tricks for evasion. For instance, a horizontal tab, a new line, or a carriage return can break up the payload and evade the detection engines.

- Horizontal tab (TAB) is `9` in hexadecimal representation
- New line (LF) is `A` in hexadecimal representation
- Carriage return (CR) is `D` in hexadecimal representation

Consequently, based on the [XSS Filter Evasion Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/XSS_Filter_Evasion_Cheat_Sheet.html), we can break up the payload. `<IMG SRC="javascript:alert('XSS');">` in various ways:

```javascript
<IMG SRC="jav&#x09;ascript:alert('XSS');">
<IMG SRC="jav&#x0A;ascript:alert('XSS');">
<IMG SRC="jav&#x0D;ascript:alert('XSS');">
```
