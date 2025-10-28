# API Building Styles
- **Representational State Transfer (REST)**: It uses a client-server model where clients make requests to resources on a server using standard HTTP methods (GET, POST, PUT, DELETE). RESTful APIs are stateless, meaning each request contains all necessary information for the server to process it, and responses are typically serialized as JSON or XML.
- **Simple Object Access Protocol (SOAP)**: Uses XML for message exchange between systems. SOAP APIs are highly standardized and offer comprehensive features for security, transactions and error handling.
- **GraphQL**: Allows clients to specify exactly what data they need, reducing over-fetching and under-fetching of data. 
- **gRPC**: Is a newer style that uses [Protocol Buffers](https://protobuf.dev/) for message serialization providing a high-performance, efficient way to communicate between systems. `gRPC` APIs can be developed in a variety of programming languages and are particularly useful for microservices and distributed systems.

## OWASP Top 10 API Security Risks
|**Risk**|**Description**|
|---|---|
|[API1:2023 - Broken Object Level Authorization](https://owasp.org/API-Security/editions/2023/en/0xa1-broken-object-level-authorization/)|The API allows authenticated users to access data they are not authorized to view.|
|[API2:2023 - Broken Authentication](https://owasp.org/API-Security/editions/2023/en/0xa2-broken-authentication/)|The authentication mechanisms of the API can be bypassed or circumvented, allowing unauthorized access.|
|[API3:2023 - Broken Object Property Level Authorization](https://owasp.org/API-Security/editions/2023/en/0xa3-broken-object-property-level-authorization/)|The API reveals sensitive data to authorized users that they should not access or permits them to manipulate sensitive properties.|
|[API4:2023 - Unrestricted Resource Consumption](https://owasp.org/API-Security/editions/2023/en/0xa4-unrestricted-resource-consumption/)|The API does not limit the amount of resources users can consume.|
|[API5:2023 - Broken Function Level Authorization](https://owasp.org/API-Security/editions/2023/en/0xa5-broken-function-level-authorization/)|The API allows unauthorized users to perform authorized operations.|
|[API6:2023 - Unrestricted Access to Sensitive Business Flows](https://owasp.org/API-Security/editions/2023/en/0xa6-unrestricted-access-to-sensitive-business-flows/)|The API exposes sensitive business flows, leading to potential financial losses and other damages.|
|[API7:2023 - Server Side Request Forgery](https://owasp.org/API-Security/editions/2023/en/0xa7-server-side-request-forgery/)|The API does not validate requests adequately, allowing attackers to send malicious requests and interact with internal resources.|
|[API8:2023 - Security Misconfiguration](https://owasp.org/API-Security/editions/2023/en/0xa8-security-misconfiguration/)|The API suffers from security misconfigurations, including vulnerabilities that lead to Injection Attacks.|
|[API9:2023 - Improper Inventory Management](https://owasp.org/API-Security/editions/2023/en/0xa9-improper-inventory-management/)|The API does not properly and securely manage version inventory.|
|[API10:2023 - Unsafe Consumption of APIs](https://owasp.org/API-Security/editions/2023/en/0xaa-unsafe-consumption-of-apis/)|The API consumes another API unsafely, leading to potential security risks.|
## Broken Object Level Authorization
Web APIs allow users to request data or records by sending various parameters, including unique identifiers such as `Universally Unique Identifiers` (`UUIDs`), also known as `Globally Unique Identifiers` (`GUIDs`), and integer IDs. However, failing to properly and securely verify that a user has ownership and permission to view a specific resource through `object-level authorization mechanisms` can lead to data exposure and security vulnerabilities.

A web API endpoint is vulnerable to `Broken Object Level Authorization` (`BOLA`), also known as `Insecure Direct Object Reference` (`IDOR`), if its authorization checks (implemented at the source-code level) fail to correctly ensure that an authenticated user has sufficient permissions or privileges to request and view specific data or perform certain operations.

## Broken Authentication
[Authentication](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html) is a fundamental pillar of web API security. Web APIs utilize various authentication mechanisms to ensure data confidentiality. An API suffers from `Broken Authentication` if any of its authentication mechanisms can be bypassed or circumvented.

# Broken Object Property Level Authorization
`Broken Object Property Level Authorization` is a category of vulnerabilities that encompasses two subclasses: `Excessive Data Exposure` and `Mass Assignment`.
An API endpoint is vulnerable to `Excessive Data Exposure` if it reveals sensitive data to authorized users that they are not supposed to access.
On the other hand, an API endpoint is vulnerable to `Mass Assignment` if it permits authorized users to manipulate sensitive object properties beyond their authorized scope, including modifying, adding, or deleting values.

# Unrestricted Resource Consumption
File upload and download are fundamental features in all applications. For instance, in e-commerce marketplaces, suppliers require the ability to upload product images, while users need to view and download these files.

A web API is vulnerable to `Unrestricted Resource Consumption` if it fails to limit user-initiated requests that consume resources such as `network bandwidth`, `CPU`, `memory`, and `storage`. These resources incur significant costs, and without adequate safeguards—particularly effective `rate-limiting`—against excessive usage, users can exploit these vulnerabilities and cause financial damage.

# Broken Function Level Authorization
A web API is vulnerable to `Broken Function Level Authorization` (`BFLA`) if it allows unauthorized or unprivileged users to interact with and invoke privileged endpoints, granting access to sensitive operations or confidential information. The difference between `BOLA` and `BFLA` is that, in the case of `BOLA`, the user is authorized to interact with the vulnerable endpoint, whereas in the case of `BFLA`, the user is not. 

# Unrestricted Access to Sensitive Business Flows
All businesses operate to generate revenue; however, if a web API exposes operations or data that allows users to abuse them and undermine the system (for example, by buying goods at a discounted price), it becomes vulnerable to `Unrestricted Access to Sensitive Business Flows`. An API endpoint is vulnerable if it exposes a sensitive business flow without appropriately restricting access to it.

# Server Side Request Forgery
A web API is vulnerable to `Server-Side Request Forgery` (`SSRF`) (also known as `Cross-Site Port Attack` (`XPSA`)) if it uses user-controlled input to fetch remote or local resources without validation. SSRF flaws occur when an API fetches a remote resource without validating the user-supplied URL. This allows an attacker to coerce the application to send a crafted request to an unexpected destination (especially local ones), bypassing firewalls or VPNs.

# Security Misconfiguration
Web APIs are susceptible to the same security misconfigurations that can compromise traditional web applications. One typical example is a web API endpoint that accepts user-controlled input and incorporates it into SQL queries without proper validation, thereby allowing [Injection](https://owasp.org/Top10/A03_2021-Injection/) attacks.
### HTTP Headers
APIs can also suffer from security misconfigurations if they do not use proper [HTTP Security Response Headers](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Headers_Cheat_Sheet.html). For example, suppose an API does not set a secure [Access-Control-Allow-Origin](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Headers_Cheat_Sheet.html#access-control-allow-origin) as part of its `CORS` (`Cross-Origin Resource Sharing`) policy. In that case, it can be exposed to security risks, most notably, [Cross-Site Request Forgery](https://cwe.mitre.org/data/definitions/352.html) (`CSRF`).
# Improper Inventory Management
Maintaining accurate and up-to-date documentation is essential for web APIs, especially considering their reliance on third-party users who need to understand how to interact with the API effectively.

However, as a web API matures and undergoes changes, it is crucial to implement proper versioning practices to avoid security pitfalls. Improper inventory management of APIs, including inadequate versioning, can introduce security misconfigurations and increase the attack surface. This can manifest in various ways, such as outdated or incompatible API versions remaining accessible, creating potential entry points for unauthorized users.
# Unsafe Consumption of APIs

APIs frequently interact with other APIs to exchange data, forming a complex ecosystem of interconnected services. While this interconnectivity enhances functionality and efficiency, it also introduces significant security risks if not managed properly. Developers may blindly trust data received from third-party APIs, especially when provided by reputable organizations, leading to relaxed security measures, particularly in input validation and data sanitization.

Several critical vulnerabilities can arise from API-to-API communication:

1. `Insecure Data Transmission`: APIs communicating over unencrypted channels expose sensitive data to interception, compromising confidentiality and integrity.
2. `Inadequate Data Validation`: Failing to properly validate and sanitize data received from external APIs before processing or forwarding it to downstream components can lead to injection attacks, data corruption, or even remote code execution.
3. `Weak Authentication`: Neglecting to implement robust authentication methods when communicating with other APIs can result in unauthorized access to sensitive data or critical functionality.
4. `Insufficient Rate-Limiting`: An API can overwhelm another API by sending a continuous surge of requests, potentially leading to denial-of-service.
5. `Inadequate Monitoring`: Insufficient monitoring of API-to-API interactions can make it difficult to detect and respond to security incidents promptly.