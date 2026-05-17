Clickjacking, or user-interface redressing, is an attack that tricks users into clicking a malicious button that has been made to look legitimate. Attackers achieve this by using HTML page-overlay techniques to hide one web page within another.
*Note: Clickjacking is rarely considered in scope for bug bounty.

Clickjacking relies on an HTML feature called `iframe`. HTML iframes allow developers to embed one web page within another by placing an `<iframe>` tag on the page, and then specifying the URL to frame in the tag's src attribute.
```html
<iframe src="https://exmaple.com" width="500" height="500"></iframe>
```
Attacker can use `iframe`s to embed real web applications on their controlled site and overlay the `iframe` on top of some real functionality. That way, if the victim is logged on the `iframe` site, the attacker can get information on it.

## Prevention
Two conditions must be met for a clickjacking vulnerability to happen. First,the vulnerable page has to have functionality that executes a state-changing action on the user's behalf. Second, the vulnerable page has to allow itself be framed by an iframe on another site.
The HTTP response header X-Frame-Options lets web pages indicate whether the page's content can be rendered in an iframe. 
```
X-Frame-Options: DENY
X-Frame-Options: SAMEORIGIN
```
The Content-Security-Policy response header is another possible defense against clickjacking.
```
Content-Security-Policy: frame ancestors 'none';
Content-Security-Policy: frame ancestors 'self' *.example.com;
```

Another way of protecting against clickjacking is with SameSite cookies.

## Hunting for Clickjacking
### Step 1. Look for State-Changing Actions
Clickjacking vulnerabilities are valuable only when the target page contains state-changing actions. You should look for pages that allow users to make changes to their accounts.
- Change passwords
- Transfer data
You should also check that the action can be achieved via clicks alone.
### Step 2. Check the Response Headers
Go through each of the state-changing functionalities and revisit the pages that containing them. See if the pages are being served with `X-Frame-Options` or `Content-Security-Policy`, if not they might be vulnerable to clickjacking. Also check if the site uses `SameSite` cookies. If it does, you won't be able to exploit a clickjacking attack on the site's features that require authentication.
### Step 3. Confirm the Vulnerability
Confirm by executing a clickjacking attack on your test account. Try changing any state through the framed page. If you can trigger the action via clicks alone through the iframe, the action is vulnerable to clickjacking.