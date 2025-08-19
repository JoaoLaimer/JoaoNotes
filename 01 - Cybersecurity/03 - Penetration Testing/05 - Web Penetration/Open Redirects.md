Website often redirects users automatically. For example, when unauthenticated users try to access protected content on a website, they are redirected to a login in page. When logged in, they're redirected back to the content they were previously trying to access.
To keep track of where to redirect the users site often uses a parameter on a URL:
`https://example.com/login?redirect=https://example.com/profile`
In this example when the user log in the app, they are redirected to a `/profile` page.

During an open-redirect attack, an attacker tricks the user into visiting an external site by providing them with a URL from the legitimate site that redirects somewhere else, like this: `https://example.com/login?redirect=https://attacker.com`.
Another common open-redirect technique is referer-based open redirect. The referer is an HTTP request header that browsers automatically include. It tells the server where the request originated from. Thus, some sites will redirect to the page's 

### Hunting for Open Redirects
#### Look for Redirect Parameters
Start by searching for the parameters used for redirects in URLs or request headers:
```
?redirect=
?redir=
?next=
...
```

Absolute URL is complete and contains all componentes necessary to locate a resource:
```
https://www.example.com/?redirect=https://www.example.com/profile
```
Relative URL must be concatenated with another URL by server in order to be used. These typically contain only the path component of a URL, like `/login`
```
https://www.example.com/?redirect=/profile
```

Also take notes on pages that don't contain redirect parameters in their URLs but still automatically redirect their users. These pages are candidates for referer-based open redirects. Look for 3XX codes like 301 and 302.

#### Use Google Dorks to Find Additional Redirect Parameters
You can use google dorks to find additional parameters, like:
```
inurl:%3Dhttp site:example.com
```
This will search for the `=` symbol on url with the `http` term. This can find hidden or non conventional redirect parameters.
Also try:
```
inurl:%3d%2f site:example.com
```
This will search for `=/`, the relative URL paths.

#### Test for Parameter-Based Open Redirects
If a redirect was found, you can test it just by simple inserting a random hostname to the parameter.
#### Test for Referer-Based Open Redirects
Test on a referer-based open redirect by hosting this HTML in your own server:
```
<html>
<a href="https://example.com/login"> CLICK </a>
</html>
```
Click the anchor, if after you interacted with the target, and you got redirected back to your site, the open redirect works.
