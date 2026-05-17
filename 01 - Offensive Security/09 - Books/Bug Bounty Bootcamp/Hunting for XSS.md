Look for user input that gets rendered on a page. Check for reflected user input.
You can also hunt for XSS in applications that communicate via non-HTTP protocols such as SMTP, SNMP, and DNS. Sometis commercial apps such as email apps and other desktop apps receive data from these protocols.

## Step 1: Look for Input Opportunities
Look for user input to the target site. Don't limit yourself to text input fields either. Sometimes drop-down menus or numeric fields can allow you to perform XSS, because even if you can't enter your payload, your proxy might let you insert it directly into the request.

Reflected and DOM XSS, look for user input in URL parameters, or path ways that get displayed to the user.  A good way to do this is to insert a custom string into each URL parameter and check.

## Step 2: Insert Payloads
Once identified, you can start inserting payloads. Use more than `<script>` tag. 
- https://portswigger.net/web-security/cross-site-scripting/cheat-sheet/.
- https://polyglot.innerht.ml/
- Use generic test string instead of XSS payloads.
- To test for Blind XSS use tools like [XSS Hunter](https://xsshunter.com/features/)
- https://owasp.org/www-community/xss-filter-evasion-cheatsheet.
## Step 3: Confirm the Impact
The impact can varie. Stored XSS on a public forum can attack anyone who visits that forum page, so stored is considered most severe. DOM and Self, require user interaction and are lower impact. The identities of the affected users matter too.