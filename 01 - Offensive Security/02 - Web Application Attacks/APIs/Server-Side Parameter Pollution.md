Some systems contain internal APIs that aren't directly accessible from the internet. Server-side parameter pollution occurs when a website embeds user input in a server-side request to an internal API without adequate encoding. This means that an attacker may be able to manipulate or inject parameters, which may enable them to, for example:

- Override existing parameters.
- Modify the application behavior.
- Access unauthorized data.

You can test any user input for any kind of parameter pollution. For example, query parameters, form fields, headers, and URL path parameters may all be vulnerable.

>This vulnerability is sometimes called HTTP parameter pollution. However, this term is also used to refer to a web application firewall (WAF) bypass technique.

## Testing for server-side parameter pollution in the query string
To test for server-side parameter pollution in the query string, place query syntax characters like `#`, `&`, and `=` in your input and observe how the application responds.
Consider a vulnerable application that enables you to search for other users based on their username. When you search for a user, your browser makes the following request:

`GET /userSearch?name=peter&back=/home`

To retrieve user information, the server queries an internal API with the following request:

`GET /users/search?name=peter&publicProfile=true`
### Truncating query strings
You can use a URL-encoded `#` character to attempt to truncate the server-side request. To help you interpret the response, you could also add a string after the `#` character.

For example, you could modify the query string to the following:

`GET /userSearch?name=peter%23foo&back=/home`

The front-end will try to access the following URL:

`GET /users/search?name=peter#foo&publicProfile=true`

> It's essential that you URL-encode the `#` character. Otherwise the front-end application will interpret it as a fragment identifier and it won't be passed to the internal API.

If the response returns the user, the server-side query may have been trauncated.
If an `Invalid Name` error message is returned, the application may have treated `foo` as part of the username. This suggests that the server-side request may not have been truncated.
If you're able to truncate the server-side request, this removes the requirement for the `publicProfile` field to be set to true. You may be able to exploit this to return non-public user profiles.

### Injecting invalid parameters
You can use an URL-encoded `&` character to attempt to add a second parameter to the server-side request.

For example, you could modify the query string to the following:

`GET /userSearch?name=peter%26foo=xyz&back=/home`

This results in the following server-side request to the internal API:

`GET /users/search?name=peter&foo=xyz&publicProfile=true`

### Injecting valid parameters
If you're able to modify the query string, you can then attempt to add a second valid parameter to the server-side request.

For example, if you've identified the `email` parameter, you could add it to the query string as follows:

`GET /userSearch?name=peter%26email=foo&back=/home`

This results in the following server-side request to the internal API:

`GET /users/search?name=peter&email=foo&publicProfile=true`

### Overriding existing parameters
To confirm whether the application is vulnerable to server-side parameter pollution, you could try to override the original parameter. Do this by injecting a second parameter with the same name.

For example, you could modify the query string to the following:

`GET /userSearch?name=peter%26name=carlos&back=/home`

This results in the following server-side request to the internal API:

`GET /users/search?name=peter&name=carlos&publicProfile=true`

The internal API interprets two `name` parameters. The impact of this depends on how the application processes the second parameter. This varies across different web technologies. For example:

- PHP parses the last parameter only. This would result in a user search for `carlos`.
- ASP.NET combines both parameters. This would result in a user search for `peter,carlos`, which might result in an `Invalid username` error message.
- Node.js / express parses the first parameter only. This would result in a user search for `peter`, giving an unchanged result.
If you're able to override the original parameter, you may be able to conduct an exploit. For example, you could add `name=administrator` to the request. This may enable you to log in as the administrator user.

#### PortSwigger Lab Example
1. In Burp's browser, trigger a password reset for the `administrator` user.
2. In **Proxy > HTTP history**, notice the `POST /forgot-password` request and the related `/static/js/forgotPassword.js` JavaScript file.
3. Right-click the `POST /forgot-password` request and select **Send to Repeater**.
4. In the **Repeater** tab, resend the request to confirm that the response is consistent.
5. Change the value of the `username` parameter from `administrator` to an invalid username, such as `administratorx`. Send the request. Notice that this results in an `Invalid username` error message.
6. Attempt to add a second parameter-value pair to the server-side request using a URL-encoded `&` character. For example, add URL-encoded `&x=y`:
    `username=administrator%26x=y`
    Send the request. Notice that this returns a `Parameter is not supported` error message. This suggests that the internal API may have interpreted `&x=y` as a separate parameter, instead of part of the username.
    
7. Attempt to truncate the server-side query string using a URL-encoded `#` character:
    
    `username=administrator%23`
    
    Send the request. Notice that this returns a `Field not specified` error message. This suggests that the server-side query may include an additional parameter called `field`, which has been removed by the `#` character.
    
8. Add a `field` parameter with an invalid value to the request. Truncate the query string after the added parameter-value pair. For example, add URL-encoded `&field=x#`:
    
    `username=administrator%26field=x%23`
    
    Send the request. Notice that this results in an `Invalid field` error message. This suggests that the server-side application may recognize the injected field parameter.
9. Brute-force the value of the `field` parameter:
    
    1. Right-click the `POST /forgot-password` request and select **Send to Intruder**.
    2. In the **Intruder** tab, add a payload position to the value of the `field` parameter as follows:
        
        `username=administrator%26field=§x§%23`
        
    3. In the **Payloads** side panel, under **Payload configuration**, click **Add from list**. Select the built-in **Server-side variable names** payload list, then start the attack.
    4. Review the results. Notice that the requests with the username and email payloads both return a `200` response.
10. Change the value of the `field` parameter from `x#` to `email`:
    
    `username=administrator%26field=email%23`
    
    Send the request. Notice that this returns the original response. This suggests that `email` is a valid field type.
11. In **Proxy > HTTP history**, review the `/static/js/forgotPassword.js` JavaScript file. Notice the password reset endpoint, which refers to the `reset_token` parameter:
    
    `/forgot-password?reset_token=${resetToken}`
12. In the **Repeater** tab, change the value of the `field` parameter from `email` to `reset_token`:
    
    `username=administrator%26field=reset_token%23`
    
    Send the request. Notice that this returns a password reset token. Make a note of this.
13. In Burp's browser, enter the password reset endpoint in the address bar. Add your password reset token as the value of the `reset_token` parameter . For example:
    
    `/forgot-password?reset_token=123456789`
14. Set a new password.
15. Log in as the `administrator` user using your password.


## Testing for server-side parameter pollution in REST paths
Consider an application that enables you to edit user profiles based on their username. Requests are sent to the following endpoint:

`GET /edit_profile.php?name=peter`

This results in the following server-side request:

`GET /api/private/users/peter`

An attacker may be able to manipulate server-side URL path parameters to exploit the API. To test for this vulnerability, add path traversal sequences to modify parameters and observe how the application responds.

You could submit URL-encoded `peter/../admin` as the value of the `name` parameter:

`GET /edit_profile.php?name=peter%2f..%2fadmin`

This may result in the following server-side request:

`GET /api/private/users/peter/../admin`

If the server-side client or back-end API normalize this path, it may be resolved to `/api/private/users/admin`.

## Testing for server-side parameter pollution in structured data formats
Consider an application that enables users to edit their profile, then applies their changes with a request to a server-side API. When you edit your name, your browser makes the following request:

`POST /myaccount name=peter`

This results in the following server-side request:

`PATCH /users/7312/update {"name":"peter"}`

You can attempt to add the `access_level` parameter to the request as follows:

`POST /myaccount name=peter","access_level":"administrator`

If the user input is added to the server-side JSON data without adequate validation or sanitization, this results in the following server-side request:

`PATCH /users/7312/update {name="peter","access_level":"administrator"}`

This may result in the user `peter` being given administrator access.

Consider a similar example, but where the client-side user input is in JSON data. When you edit your name, your browser makes the following request:

`POST /myaccount {"name": "peter"}`

This results in the following server-side request:

`PATCH /users/7312/update {"name":"peter"}`

You can attempt to add the `access_level` parameter to the request as follows:

`POST /myaccount {"name": "peter\",\"access_level\":\"administrator"}`

If the user input is decoded, then added to the server-side JSON data without adequate encoding, this results in the following server-side request:

`PATCH /users/7312/update {"name":"peter","access_level":"administrator"}`

Again, this may result in the user `peter` being given administrator access.