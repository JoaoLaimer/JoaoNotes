Authentication process that allows a user to access multiple applications or websites by logging in only once with a single set of credentials
SSO works base on a trusted relation that is establishment between an application and an Identity Provider
- Improve user experience
- Increased productivity
- Reduced information technology support costs
- Enhanced security
## Identity Provider (IdP)
System that creates, maintains, and manages identity information for principals while providing authentication services to relying applications within a federation or distributed network.

## Lightweight Directory Access Protocol (LDAP)
Used to access and maintain distributed directory information services over an Internet protocol network.
An organization might use use LDAP to form a directory of its employees.
LDAP is also used to in authentication and server as a central repository for user information.
> Directory services, such as Microsoft Active Directory Domain Services (ADDS), proide authentication and authorization services for a network. ADDS uses LDAP, encrypted with TLS when querying the directory. 
## Open Authorization (OAuth)
Open standard for token-based authentication and authorization that allows an individual's account information to be used by third-party services without exposing the user's password.
OAuth protocol is commonly used for authentication and authorization in RESTful APIs.
The client app or service registers with the authorization server, provides a redirect URL, and gets an ID and secret.
> Implementing a central OAuth authorization server to handle user authentication and issue access tokens to third-party applications is the most effective way to implement OAuth.

> It's easy to get confused about what OAuth does because the name is ambiguous! Remember that the "Auth" in OAuth stands for authorization, not authentication!
## Security Assertion Markup Language (SAML)
A standard for logging users into applications based on their sessions in another context.
SAML allows services to separate from identity providers and removes the need for direct user authentication.
> SAML is an XML-based standard used to exchange authentication and authorization information between different parties. SAML provides SSO for web-based application.

