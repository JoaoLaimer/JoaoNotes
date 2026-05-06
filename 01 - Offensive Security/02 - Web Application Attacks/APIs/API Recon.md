# API documentation

Even if API documentation isn't openly available, you may still be able to access it by browsing applications that use the API.

To do this, you can use Burp Scanner to crawl the API. You can also browse applications manually using Burp's browser. Look for endpoints that may refer to API documentation, for example:
- `/api`
- `/swagger/index.html`
- `/openapi.json`
If you identify an endpoint for a resource, make sure to investigate the base path. For example, if you identify the resource endpoint `/api/swagger/v1/users/123`, then you should investigate the following paths:
- `/api/swagger/v1`
- `/api/swagger`
- `/api`
### Using machine-readable documentation

You can use a range of automated tools to analyze any machine-readable API documentation that you find.

You can use Burp Scanner to crawl and audit OpenAPI documentation, or any other documentation in JSON or YAML format. You can also parse OpenAPI documentation using the [OpenAPI Parser](https://portswigger.net/bappstore/6bf7574b632847faaaa4eb5e42f1757c) BApp.

You may also be able to use a specialized tool to test the documented endpoints, such as [Postman](https://www.postman.com/) or [SoapUI](https://www.soapui.org/).
# Interacting with API endpoints
## Identifying supported HTTP methods
An API endpoint may support different HTTP methods. It's therefore important to test all potential methods when you're investigating API endpoints. This may enable you to identify additional endpoint functionality, opening up more attack surface.

For example, the endpoint `/api/tasks` may support the following methods:

- `GET /api/tasks` - Retrieves a list of tasks.
- `POST /api/tasks` - Creates a new task.
- `DELETE /api/tasks/1` - Deletes a task.
## Common HTTP Methods

- **GET**: Requests a representation of a specific resource. It is the most common method, used simply to retrieve data without changing anything on the server.
- **POST**: Submits data to be processed by the server, often resulting in the creation of a new resource or a change in state.
- **PUT**: Replaces all current representations of the target resource with the uploaded content. If the resource doesn't exist, it can create a new one.
- **PATCH**: Applies partial modifications to a resource, making it more efficient than **PUT** for small changes.
- **DELETE**: Removes the specified resource from the server.
- **HEAD**: Identical to **GET** but requests only the response headers without the body. This is useful for checking a resource's size or if it has been modified.
- **OPTIONS**: Asks the server which HTTP methods are permitted for a specific URL.
- **CONNECT**: Used to establish a network tunnel, typically for secure [HTTPS connections](https://www.cloudflare.com/learning/ddos/glossary/hypertext-transfer-protocol-http/) through a proxy.
- **TRACE**: Performs a loop-back test, echoing the request back so the client can see what changes intermediaries (like proxies) have made.
## Identifying supported content types
API endpoints often expect data in a specific format. They may therefore behave differently depending on the content type of the data provided in a request. Changing the content type may enable you to:

- Trigger errors that disclose useful information.
- Bypass flawed defenses.
- Take advantage of differences in processing logic. For example, an API may be secure when handling JSON data but susceptible to injection attacks when dealing with XML.

To change the content type, modify the `Content-Type` header, then reformat the request body accordingly.
## Finding hidden parameters

When you're doing API recon, you may find undocumented parameters that the API supports. You can attempt to use these to change the application's behavior. 
- The [Param miner](https://portswigger.net/bappstore/17d2949a985c4b7ca092728dba871943) BApp enables you to automatically guess up to 65,536 param names per request. Param miner automatically guesses names that are relevant to the application, based on information taken from the scope.

### Mass assignment vulnerabilities
Mass assignment (also known as auto-binding) can inadvertently create hidden parameters. It occurs when software frameworks automatically bind request parameters to fields on an internal object. Mass assignment may therefore result in the application supporting parameters that were never intended to be processed by the developer.
#### Identifying hidden parameters

Since mass assignment creates parameters from object fields, you can often identify these hidden parameters by manually examining objects returned by the API.

For example, consider a `PATCH /api/users/` request, which enables users to update their username and email, and includes the following JSON:

`{ "username": "wiener", "email": "wiener@example.com", }`

A concurrent `GET /api/users/123` request returns the following JSON:

```JSON
{ 
   "id": 123,
   "name": "John Doe",
   "email": "john@example.com",
   "isAdmin": "false" 
}
```

This may indicate that the hidden `id` and `isAdmin` parameters are bound to the internal user object, alongside the updated username and email parameters.

#### Testing mass assignment vulnerabilities
To test whether you can modify the enumerated `isAdmin` parameter value, add it to the `PATCH` request:

```JSON
{ 
   "username": "wiener",
   "email": "wiener@example.com",
   "isAdmin": false, 
}
```
In addition, send a `PATCH` request with an invalid `isAdmin` parameter value:

```JSON
{ 
   "username": "wiener",
   "email": "wiener@example.com",
   "isAdmin": "foo", 
}
```
If the application behaves differently, this may suggest that the invalid value impacts the query logic, but the valid value doesn't. This may indicate that the parameter can be successfully updated by the user. 
You can then send a `PATCH` request with the `isAdmin` parameter value set to `true`, to try and exploit the vulnerability.