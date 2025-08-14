Website often redirects users automatically. For example, when unauthenticated users try to access protected content on a website, they are redirected to a login in page. When logged in, they're redirected back to the content they were previously trying to access.
To keep track of where to redirect the users site often uses a parameter on a URL:
`https://example.com/login?redirect=https://example.com/profile`
In this example when the user log in the app, they are redirected to a `/profile` page.

During an open-redirect attack, an attacker tricks the user into visiting an external site by providing them with a URL from the legitimate site that redirects somewhere else, like this: `https://example.com/login?redirect=https://attacker.com`.
Another common open-redirect technique is referer-based open redirect. The referer is an HTTP request header that browsers automatically include. It tells the server where the request originated from. Thus, some sites will redirect to the page's 