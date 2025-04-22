# Key Concepts
## Resource Owner
The person or system that controls certain data and can authorize an application to access that data on their behalf.
## Client
The client can be a mobile app or a server-side web application. It acts as an intermediary, requesting access to resources and performing action as permitted by the resource owner. he authorization server plays a crucial role in the OAuth process by ensuring the client is granted permission only after legitimate user authentication and consent.
## Resource Server
The server hosting the resources can accept and respond to protected resources requests using access tokens.
## Authorization Grant
The client uses a credential representing the resource owner's authorization to obtain an access token. The main grant types are `Authotization Code`, `Implicit`, `Resource Owner Password Credentials`, and `Client Credentials`.
## Access Token
A credential that the client can use to access protected resources on behalf of the resource owner. It has a limited lifespan and scope. 
## Refresh Token
A credential that the client can use to obtain a new access token without requiring the resource owner to re-authenticate.
## Redirect URI
The URI to which the authorization server will redirect the resource owner's user-agent after the grant or denial of the authentication.
## Scope 
Scopes limit the application access to a user account. They allow the client to specify the lever of access needed and the authorization server to inform the user what access levels the application is requesting.
## State Parameter
An optional parameter maintains the state between the client and the authorization server. It can help prevent CSRF (Cross-site request forgery) attacks by ensuring the response matches the client's request. The state parameter is a crucial part of securing the OAuth flow.
## Token & Authorization Endpoint
The authorization server's endpoint is where the client exchanges the authorization grant (or refresh token) for an access token. In contrast, the authorization endpoint is where the resource owner is authenticated and authorizes the client to access the protected resources.

# Grant Types
### Authorization Code Grant
Most commonly used OAuth 2.0 flow suited for server-side applications. In this flow, the client redirects the user to the authorization server, where the user authenticates and grants authorization. 
This grant type is known for its enhanced security, as the authorization code is exchanged for an access token server-to-server, meaning the access token is not exposed to the user agent (e.g., browser), thus reducing the risk of token leakage. It also supports using refresh tokens to maintain long-term access without repeated user authentication.
## Implicit Grant
Is design for mobile and web application where clients cannot securely store secrets. It directly issues the access token to the client without requiring an authorization code exchange. In this flow, the client redirects the user to the authorization server. After the user authenticates and grants authorization, the authorization server return an access token in the URL fragment.
This grant is simplified and suitable for clients who cannot securely store client secrets. It also does not support refresh tokens.
## Resource Owner Password Credentials Grant
Used when the client is highly trusted by the resource owner, such as first-party applications. The client collects the user's credentials directly and exchanges them for an access token.
In this flow, the user provides their credentials directly to the client. The client then sends the credentials to the authorization server, which verifies the credentials and issues an access token. This grant type is direct, requiring fewer interactions, making it suitable for highly trusted applications where the user is confident in providing their credentials. However, it is less secure because it involves sharing credentials directly with the client and is unsuitable for third-party applications.
## Client Credentials Grant
The Client Credentials grant is used for server-to-server interactions without user involvement. The client uses his credentials to authenticate with the authorization server and obtain an access token. In this flow, the client authenticates with the authorization server using its client credentials (client ID and secret), and the authorization server issues an access token directly to the client.
This grant type is suitable for backend services and server-to-server communication as it does not involve user credentials, thus reducing security risks related to user data exposure.